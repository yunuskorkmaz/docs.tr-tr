---
title: 'Nasıl yapılır: Özel WSDL İçe Aktarma'
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: 33762afffca6e90cb32c358bee6d9f29ca609994
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488276"
---
# <a name="how-to-import-custom-wsdl"></a>Nasıl yapılır: Özel WSDL İçe Aktarma
Bu konu, özel WSDL içe aktarmayı açıklar. Özel WSDL işlemek için uygulamanız gereken <xref:System.ServiceModel.Description.IWsdlImportExtension> arabirimi.  
  
### <a name="to-import-custom-wsdl"></a>Özel WSDL içe aktarmak için  
  
1.  Uygulama <xref:System.ServiceModel.Description.IWsdlImportExtension>. Uygulama <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> içeri aktarılmadan önce meta verileri değiştirmeye yöntemi. Uygulama <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> ve <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> sözleşmeleri ve meta verileri içe uç noktalarını değiştirmek için yöntemleri. İçeri aktarılan sözleşme veya uç nokta erişmek için karşılık gelen bağlam nesnesi kullanın (<xref:System.ServiceModel.Description.WsdlContractConversionContext> veya <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):  
  
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
  
2.  Özel WSDL alma aracını kullanmak için istemci uygulaması yapılandırın. Svcutil.exe kullanıyorsanız, bu yapılandırma yapılandırma dosyasına Svcutil.exe (Svcutil.exe.config) eklemeniz gerektiğini unutmayın:  
  
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
  
3.  Yeni bir <xref:System.ServiceModel.Description.WsdlImporter> örneği (tümleştirilmesidir <xref:System.ServiceModel.Description.MetadataSet> içeri aktarmak istediğiniz WSDL belgeleri içeren örneği) ve arama <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);          System.Collections.ObjectModel.Collection<ContractDescription> contracts  = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veriler](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [Meta Verileri Dışarı ve İçeri Aktarma](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)  
 [Özel WSDL Yayımı](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)
