---
title: 'Nasıl yapılır: Özel WSDL İçeri Aktarma'
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: 930cb92d8193ba3ffc1f62191f2012e104091190
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796994"
---
# <a name="how-to-import-custom-wsdl"></a>Nasıl yapılır: Özel WSDL İçeri Aktarma
Bu konu başlığı altında, özel WSDL 'nin nasıl içeri aktarılacağı açıklanmaktadır. Özel wsdl 'yi işlemek için <xref:System.ServiceModel.Description.IWsdlImportExtension> arabirimini uygulamanız gerekir.  
  
### <a name="to-import-custom-wsdl"></a>Özel WSDL 'yi içeri aktarmak için  
  
1. Uygulayın <xref:System.ServiceModel.Description.IWsdlImportExtension>. İçeri aktarmadan önce meta verileri değiştirmek için yönteminiuygulayın.<xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> Meta verilerden içeri <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> aktarılan sözleşmeleri ve uç noktaları değiştirmek için veyöntemleriniuygulayın.<xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> İçeri aktarılan sözleşmeye veya uç noktaya erişmek için, karşılık gelen bağlam nesnesini kullanın<xref:System.ServiceModel.Description.WsdlContractConversionContext> ( <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>veya):  
  
    ```  
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
  
2. İstemci uygulamasını özel WSDL İçeri Aktarıcı kullanacak şekilde yapılandırın. Svcutil. exe kullanıyorsanız, bu yapılandırmayı Svcutil. exe (Svcutil. exe. config) yapılandırma dosyasına eklemeniz gerektiğini unutmayın:  
  
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
  
3. Yeni <xref:System.ServiceModel.Description.WsdlImporter> bir örnek oluşturun (içeri aktarmak istediğiniz <xref:System.ServiceModel.Description.MetadataSet> WSDL belgelerini içeren örneği geçirerek) ve şunu çağırın <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);          System.Collections.ObjectModel.Collection<ContractDescription> contracts  = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veriler](../feature-details/metadata.md)
- [Meta Verileri Dışarı ve İçeri Aktarma](../feature-details/exporting-and-importing-metadata.md)
- [Özel WSDL Yayımı](../samples/custom-wsdl-publication.md)
