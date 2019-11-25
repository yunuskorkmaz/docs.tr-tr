---
title: 'Nasıl yapılır: Özel WSDL İçe Aktarma'
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: 10fc3282560d35e61044a367f8172571096d76bd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975897"
---
# <a name="how-to-import-custom-wsdl"></a><span data-ttu-id="10fab-102">Nasıl yapılır: Özel WSDL İçe Aktarma</span><span class="sxs-lookup"><span data-stu-id="10fab-102">How to: Import Custom WSDL</span></span>
<span data-ttu-id="10fab-103">Bu konu başlığı altında, özel WSDL 'nin nasıl içeri aktarılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10fab-103">This topic describes how to import custom WSDL.</span></span> <span data-ttu-id="10fab-104">Özel WSDL 'yi işlemek için <xref:System.ServiceModel.Description.IWsdlImportExtension> arabirimini uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="10fab-104">To handle the custom WSDL, you must implement the <xref:System.ServiceModel.Description.IWsdlImportExtension> interface.</span></span>  
  
### <a name="to-import-custom-wsdl"></a><span data-ttu-id="10fab-105">Özel WSDL 'yi içeri aktarmak için</span><span class="sxs-lookup"><span data-stu-id="10fab-105">To import custom WSDL</span></span>  
  
1. <span data-ttu-id="10fab-106"><xref:System.ServiceModel.Description.IWsdlImportExtension>uygulayın.</span><span class="sxs-lookup"><span data-stu-id="10fab-106">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span></span> <span data-ttu-id="10fab-107">Verilerin içeri aktarılmadan önce değiştirilmesi için <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> yöntemini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="10fab-107">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> method to modify the metadata before it is imported.</span></span> <span data-ttu-id="10fab-108">Meta verilerden içeri aktarılan sözleşmeleri ve uç noktaları değiştirmek için <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> ve <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> yöntemlerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="10fab-108">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> and <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> methods to modify contracts and endpoints imported from the metadata.</span></span> <span data-ttu-id="10fab-109">İçeri aktarılan sözleşmeye veya uç noktaya erişmek için, karşılık gelen bağlam nesnesini kullanın (<xref:System.ServiceModel.Description.WsdlContractConversionContext> veya <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span><span class="sxs-lookup"><span data-stu-id="10fab-109">To access the imported contract or endpoint, use the corresponding context object (<xref:System.ServiceModel.Description.WsdlContractConversionContext> or <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span></span>  
  
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
  
2. <span data-ttu-id="10fab-110">İstemci uygulamasını özel WSDL İçeri Aktarıcı kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="10fab-110">Configure the client application to use the custom WSDL importer.</span></span> <span data-ttu-id="10fab-111">Svcutil. exe kullanıyorsanız, bu yapılandırmayı Svcutil. exe (Svcutil. exe. config) yapılandırma dosyasına eklemeniz gerektiğini unutmayın:</span><span class="sxs-lookup"><span data-stu-id="10fab-111">Note that if you are using Svcutil.exe, you should add this configuration to the configuration file for Svcutil.exe (Svcutil.exe.config):</span></span>  
  
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
  
3. <span data-ttu-id="10fab-112">Yeni bir <xref:System.ServiceModel.Description.WsdlImporter> örneği oluşturun (içeri aktarmak istediğiniz WSDL belgelerini içeren <xref:System.ServiceModel.Description.MetadataSet> örneğini geçirerek) ve <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>çağırın:</span><span class="sxs-lookup"><span data-stu-id="10fab-112">Create a new <xref:System.ServiceModel.Description.WsdlImporter> instance (passing in the <xref:System.ServiceModel.Description.MetadataSet> instance that contains the WSDL documents that you want to import), and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span></span>  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="10fab-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10fab-113">See also</span></span>

- [<span data-ttu-id="10fab-114">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="10fab-114">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="10fab-115">Meta Verileri Dışarı ve İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="10fab-115">Exporting and Importing Metadata</span></span>](../feature-details/exporting-and-importing-metadata.md)
- [<span data-ttu-id="10fab-116">Özel WSDL Yayımı</span><span class="sxs-lookup"><span data-stu-id="10fab-116">Custom WSDL Publication</span></span>](../samples/custom-wsdl-publication.md)
