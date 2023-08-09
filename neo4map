const neo4j = require('neo4j-driver');

exports.handler = async () => {
  const driver = neo4j.driver(
    'neo4j+s://a4edc8f1.databases.neo4j.io:7687',
    neo4j.auth.basic('neo4j', 'PF0dZPwVi8Q79WH265v-BepG66MjvWpHSJ25_kuRCuw')
  );

  const session = driver.session();
  const result = await session.run(`
    MATCH (city:City)
    RETURN city.name AS cityName
  `);

  session.close();
  driver.close();

  return {
    statusCode: 200,
    body: JSON.stringify(result.records.map(record => record.get('cityName')))
  };
};
