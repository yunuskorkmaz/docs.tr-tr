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
# <a name="how-to-import-custom-wsdl"></a><span data-ttu-id="489c3-102">Nasıl yapılır: Özel WSDL İçe Aktarma</span><span class="sxs-lookup"><span data-stu-id="489c3-102">How to: Import Custom WSDL</span></span>
<span data-ttu-id="489c3-103">Bu konu, özel WSDL içe aktarmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="489c3-103">This topic describes how to import custom WSDL.</span></span> <span data-ttu-id="489c3-104">Özel WSDL işlemek için uygulamanız gereken <xref:System.ServiceModel.Description.IWsdlImportExtension> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="489c3-104">To handle the custom WSDL, you must implement the <xref:System.ServiceModel.Description.IWsdlImportExtension> interface.</span></span>  
  
### <a name="to-import-custom-wsdl"></a><span data-ttu-id="489c3-105">Özel WSDL içe aktarmak için</span><span class="sxs-lookup"><span data-stu-id="489c3-105">To import custom WSDL</span></span>  
  
1.  <span data-ttu-id="489c3-106">Uygulama <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span><span class="sxs-lookup"><span data-stu-id="489c3-106">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span></span> <span data-ttu-id="489c3-107">Uygulama <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> içeri aktarılmadan önce meta verileri değiştirmeye yöntemi.</span><span class="sxs-lookup"><span data-stu-id="489c3-107">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> method to modify the metadata before it is imported.</span></span> <span data-ttu-id="489c3-108">Uygulama <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> ve <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> sözleşmeleri ve meta verileri içe uç noktalarını değiştirmek için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="489c3-108">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> and <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> methods to modify contracts and endpoints imported from the metadata.</span></span> <span data-ttu-id="489c3-109">İçeri aktarılan sözleşme veya uç nokta erişmek için karşılık gelen bağlam nesnesi kullanın (<xref:System.ServiceModel.Description.WsdlContractConversionContext> veya <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span><span class="sxs-lookup"><span data-stu-id="489c3-109">To access the imported contract or endpoint, use the corresponding context object (<xref:System.ServiceModel.Description.WsdlContractConversionContext> or <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span></span>  
  
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
  
2.  <span data-ttu-id="489c3-110">Özel WSDL alma aracını kullanmak için istemci uygulaması yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="489c3-110">Configure the client application to use the custom WSDL importer.</span></span> <span data-ttu-id="489c3-111">Svcutil.exe kullanıyorsanız, bu yapılandırma yapılandırma dosyasına Svcutil.exe (Svcutil.exe.config) eklemeniz gerektiğini unutmayın:</span><span class="sxs-lookup"><span data-stu-id="489c3-111">Note that if you are using Svcutil.exe, you should add this configuration to the configuration file for Svcutil.exe (Svcutil.exe.config):</span></span>  
  
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
  
3.  <span data-ttu-id="489c3-112">Yeni bir <xref:System.ServiceModel.Description.WsdlImporter> örneği (tümleştirilmesidir <xref:System.ServiceModel.Description.MetadataSet> içeri aktarmak istediğiniz WSDL belgeleri içeren örneği) ve arama <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span><span class="sxs-lookup"><span data-stu-id="489c3-112">Create a new <xref:System.ServiceModel.Description.WsdlImporter> instance (passing in the <xref:System.ServiceModel.Description.MetadataSet> instance that contains the WSDL documents that you want to import), and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);          System.Collections.ObjectModel.Collection<ContractDescription> contracts  = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="489c3-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="489c3-113">See Also</span></span>  
 [<span data-ttu-id="489c3-114">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="489c3-114">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="489c3-115">Meta Verileri Dışarı ve İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="489c3-115">Exporting and Importing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)  
 [<span data-ttu-id="489c3-116">Özel WSDL Yayımı</span><span class="sxs-lookup"><span data-stu-id="489c3-116">Custom WSDL Publication</span></span>](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)
