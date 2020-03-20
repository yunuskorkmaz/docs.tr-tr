---
title: 'Nasıl yapılır: Özel WSDL İçe Aktarma'
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: 614842f2d77d967e0a6d4841e5e5e4fcc8805580
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185542"
---
# <a name="how-to-import-custom-wsdl"></a>Nasıl yapılır: Özel WSDL İçe Aktarma
Bu konu, özel WSDL'nin nasıl içe aktarılabildiğini açıklar. Özel WSDL işlemek için <xref:System.ServiceModel.Description.IWsdlImportExtension> arabirimi uygulamanız gerekir.  
  
### <a name="to-import-custom-wsdl"></a>Özel WSDL almak için  
  
1. Uygulayın. <xref:System.ServiceModel.Description.IWsdlImportExtension> Meta <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> verileri aktarılmadan önce değiştirmek için yöntemi uygulayın. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> Meta verilerden alınan sözleşmeleri ve uç noktaları değiştirmek için <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> ve yöntemleri uygulayın. İçe aktarılan sözleşmeye veya bitiş noktasına erişmek<xref:System.ServiceModel.Description.WsdlContractConversionContext> <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>için ilgili bağlam nesnesini (veya):  
  
    ```csharp
    public class WsdlDocumentationImporter : IWsdlImportExtension
    {
        public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)
        {
            // Contract documentation
            if (context.WsdlPortType.Documentation != null)
            {
                context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));
            }
            // Operation documentation
            foreach (Operation operation in context.WsdlPortType.Operations)
            {
                if (operation.Documentation != null)
                {
                    OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);
                    if (operationDescription != null)
                    {
                        operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));
                    }
                }
            }
        }

        public void BeforeImport(ServiceDescriptionCollection wsdlDocuments, XmlSchemaSet xmlSchemas, ICollection<XmlElement> policy)
        {
            Console.WriteLine("BeforeImport called.");
        }

        public void ImportEndpoint(WsdlImporter importer, WsdlEndpointConversionContext context)
        {
            Console.WriteLine("ImportEndpoint called.");
        }
    }
    ```
  
2. Özel WSDL içe aktarıcısını kullanacak şekilde istemci uygulamasını yapılandırın. Svcutil.exe kullanıyorsanız, bu yapılandırmayı Svcutil.exe (Svcutil.exe.config) için yapılandırma dosyasına eklemeniz gerektiğini unutmayın:  
  
    ```xml  
    <system.serviceModel>  
          <client>  
            <endpoint
              address="http://localhost:8000/Fibonacci"
              binding="wsHttpBinding"  
              contract="IFibonacci"  
            />  
            <metadata>  
              <wsdlImporters>  
                <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
              </wsdlImporters>  
            </metadata>  
          </client>  
        </system.serviceModel>  
    ```  
  
3. Yeni <xref:System.ServiceModel.Description.WsdlImporter> bir örnek oluşturun <xref:System.ServiceModel.Description.MetadataSet> (almak istediğiniz WSDL belgelerini içeren örnekte <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>geçerek) ve şu çağrıda bulunuyor:  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta veriler](../feature-details/metadata.md)
- [Meta Verileri Dışarı ve İçeri Aktarma](../feature-details/exporting-and-importing-metadata.md)
- [Özel WSDL Yayımı](../samples/custom-wsdl-publication.md)
