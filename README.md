# CustomPakageAI
Ejemplos y resumen de la configuración de un Custom Package (phython) para AI Center.

#Custom Package en AI Center

##  Estructura del .zip (mlpackagelocaldepend.zip)
mlpackagelocaldepend
 |- on_prem_dependencies
    |- example_tester-0.1.0-py3-none-any.whl
 main.py
 requeriments.txt

## Código de prueba con dependencia

requirements.txt

    --find-links ./on_prem_dependencies
    --no-index
    example_tester


main.py

    from example_tester import ExampleTester

    class Main:
        def __init__(self):
            self.tester = ExampleTester()

        def predict(self, X):
            self.tester.print_working_directory()
            return "{""status"": ""Working""}"
        
        
    if __name__ == "__main__":
        tester = ExampleTester()
        tester.print_working_directory()

## Testing

Para obtener la respuesta de la Skill de aicenter desplegada
- Llamada:

  curl -H "Content-Type: application/json" -d "{\"p1\":\"Hola\"}" https://uipath-ai.sscc.ae.aena.es/public/mlskills/host/36c79fd5-6d99-4ccb-84f6-31ecd44fbd9c/mlskill-jcv

- Respuesta: 
  {status: Working}
