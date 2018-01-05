---
title: "Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e50ddaa5a9fe5038ef167c4a53f9600eda0f027
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a><span data-ttu-id="ece81-102">Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma</span><span class="sxs-lookup"><span data-stu-id="ece81-102">How to: Use Svcutil.exe to Export Metadata from Compiled Service Code</span></span>
<span data-ttu-id="ece81-103">Svcutil.exe gibi hizmetleri, sözleşmeler ve derlenmiş derlemelerde veri türlerini için meta verileri dışarı aktarabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ece81-103">Svcutil.exe can export metadata for services, contracts, and data types in compiled assemblies, as follows:</span></span>  
  
-   <span data-ttu-id="ece81-104">Tüm meta verilerini aktarmak için Svcutil.exe, kullanarak derlemeler kümesi için hizmet sözleşmeleri derlenmiş giriş parametreleri olarak derlemeler belirtin.</span><span class="sxs-lookup"><span data-stu-id="ece81-104">To export metadata for all compiled service contracts for a set of assemblies using Svcutil.exe, specify the assemblies as input parameters.</span></span> <span data-ttu-id="ece81-105">Bu varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="ece81-105">This is the default behavior.</span></span>  
  
-   <span data-ttu-id="ece81-106">Svcutil.exe kullanarak derlenmiş bir hizmet için meta verileri dışarı aktarmak için hizmet derleme veya derlemelerin giriş parametreleri olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="ece81-106">To export metadata for a compiled service using Svcutil.exe, specify the service assembly or assemblies as input parameters.</span></span> <span data-ttu-id="ece81-107">Kullanmalısınız `/serviceName` vermek istediğiniz hizmet yapılandırma adını belirtmek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ece81-107">You must use the `/serviceName` option to indicate the configuration name of the service you want to export.</span></span> <span data-ttu-id="ece81-108">Svcutil.exe yapılandırma dosyası için belirtilen çalıştırılabilir derlemeyi otomatik olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="ece81-108">Svcutil.exe automatically loads the configuration file for the specified executable assembly.</span></span>  
  
-   <span data-ttu-id="ece81-109">Derlemeler kümesini içindeki tüm veri sözleşme türleri dışarı aktarmak için kullanın `/dataContractOnly` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ece81-109">To export all data contract types within a set of assemblies, use the `/dataContractOnly` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ece81-110">Kullanım `/reference` seçeneği tüm bağımlı derlemeler için dosya yolunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="ece81-110">Use the `/reference` option to specify the file paths to any dependent assemblies.</span></span>  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a><span data-ttu-id="ece81-111">Meta verileri derlenmiş Hizmet sözleşmeleri için dışarı aktarmak için</span><span class="sxs-lookup"><span data-stu-id="ece81-111">To export metadata for compiled service contracts</span></span>  
  
1.  <span data-ttu-id="ece81-112">Bir veya daha fazla sınıf libraries.1 halinde, hizmet sözleşmesi uygulamaları derleme</span><span class="sxs-lookup"><span data-stu-id="ece81-112">Compile your service contract implementations into one or more class libraries.1</span></span>  
  
2.  <span data-ttu-id="ece81-113">Svcutil.exe derlenmiş derlemelerini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ece81-113">Run Svcutil.exe on the compiled assemblies.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ece81-114">Kullanmanız gerekebilir `/reference` anahtar herhangi bir bağımlı derleme dosya yolunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="ece81-114">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a><span data-ttu-id="ece81-115">Derlenmiş bir hizmet için meta verileri dışarı aktarmak için</span><span class="sxs-lookup"><span data-stu-id="ece81-115">To export metadata for a compiled service</span></span>  
  
1.  <span data-ttu-id="ece81-116">Yürütülebilir bir bütünleştirilmiş hizmet uygulamanızı derleyin.</span><span class="sxs-lookup"><span data-stu-id="ece81-116">Compile your service implementation into an executable assembly.</span></span>  
  
2.  <span data-ttu-id="ece81-117">Hizmeti yürütülebilir dosyası için bir yapılandırma dosyası oluşturun ve bir hizmet yapılandırması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ece81-117">Create a configuration file for your service executable and add a service configuration.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="MyService" >  
            <endpoint address="finder" contract="IPeopleFinder" binding="wsHttpBinding" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
3.  <span data-ttu-id="ece81-118">Svcutil.exe derlenmiş hizmet yürütülebilir kullanarak çalıştırın `/serviceName` anahtar hizmetin yapılandırma adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="ece81-118">Run Svcutil.exe on the compiled service executable using the `/serviceName` switch to specify the configuration name of the service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ece81-119">Kullanmanız gerekebilir `/reference` anahtar herhangi bir bağımlı derleme dosya yolunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="ece81-119">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a><span data-ttu-id="ece81-120">Derlenmiş veri sözleşmeleri için meta verileri dışarı aktarmak için</span><span class="sxs-lookup"><span data-stu-id="ece81-120">To export metadata for compiled data contracts</span></span>  
  
1.  <span data-ttu-id="ece81-121">Veri sözleşmesi uygulamaları bir veya daha fazla sınıf kitaplıkları içine derleyin.</span><span class="sxs-lookup"><span data-stu-id="ece81-121">Compile your data contract implementations into one or more class libraries.</span></span>  
  
2.  <span data-ttu-id="ece81-122">Kullanarak derlenmiş derlemeler svcutil.exe çalıştırmak `/dataContract` yalnızca meta verilerin veri sözleşmeleri üretilmesi gerektiğini belirtmek için anahtar.</span><span class="sxs-lookup"><span data-stu-id="ece81-122">Run Svcutil.exe on the compiled assemblies using the `/dataContract` switch to specify that only metadata for data contracts should be generated.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ece81-123">Kullanmanız gerekebilir `/reference` anahtar herhangi bir bağımlı derleme dosya yolunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="ece81-123">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a><span data-ttu-id="ece81-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="ece81-124">Example</span></span>  
 <span data-ttu-id="ece81-125">Aşağıdaki örnek, bir basit hizmeti uygulama ve yapılandırma meta verilerini oluşturmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ece81-125">The following example demonstrates how to generate metadata for a simple service implementation and configuration.</span></span>  
  
 <span data-ttu-id="ece81-126">Hizmet sözleşmesi için meta verileri dışarı aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="ece81-126">To export metadata for the service contract.</span></span>  
  
```  
svcutil.exe Contracts.dll  
```  
  
 <span data-ttu-id="ece81-127">Veri sözleşmeleri için meta verileri dışarı aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="ece81-127">To export metadata for the data contracts.</span></span>  
  
```  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 <span data-ttu-id="ece81-128">Hizmet uygulaması için meta verileri dışarı aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="ece81-128">To export metadata for the service implementation.</span></span>  
  
```  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 <span data-ttu-id="ece81-129">`<path>` Contracts.dll yoludur.</span><span class="sxs-lookup"><span data-stu-id="ece81-129">The `<path>` is the path to Contracts.dll.</span></span>  
  
```  
// The following service contract and data contracts are compiled into   
// Contracts.dll.  
[ServiceContract(ConfigurationName="IPeopleFinder")]  
public interface IPersonFinder  
{  
    [OperationContract]  
    Address GetAddress(Person s);  
}  
  
[DataContract]  
public class Person  
{  
    [DataMember]  
    public string firstName;  
    [DataMember]  
    public string lastName;  
    [DataMember]  
    public int age;  
}  
  
[DataContract]  
public class Address  
{  
    [DataMember]  
    public string city;  
    [DataMember]  
    public string state;  
    [DataMember]  
    public string street;  
    [DataMember]  
    public int zipCode;  
    [DataMember]  
    public Person person;  
}  
  
// The following service implementation is compiled into Service.exe.     
// This service uses the contracts specified in Contracts.dll.  
[ServiceBehavior(ConfigurationName = "MyService")]  
public class MyService : IPersonFinder  
{  
    public Address GetAddress(Person person)  
    {  
        Address address = new Address();  
        address.person = person;  
        return address;  
    }  
}  
  
<!-- The following is the configuration file for Service.exe. -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="MyService">  
         <endpoint  address="finder"  
                    binding="basicHttpBinding"  
                    contract="IPeopleFinder"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ece81-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ece81-130">See Also</span></span>  
 [<span data-ttu-id="ece81-131">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="ece81-131">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="ece81-132">Meta Verileri Dışarı ve İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="ece81-132">Exporting and Importing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
