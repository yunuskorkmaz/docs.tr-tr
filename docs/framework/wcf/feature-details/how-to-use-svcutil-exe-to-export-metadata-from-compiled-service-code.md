---
title: 'Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: 9acefdec63a6f518ead6cdbcb19ebc8c75609dd6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595368"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a><span data-ttu-id="94065-102">Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma</span><span class="sxs-lookup"><span data-stu-id="94065-102">How to: Use Svcutil.exe to Export Metadata from Compiled Service Code</span></span>
<span data-ttu-id="94065-103">Svcutil. exe, derlenmiş derlemelerde hizmetler, sözleşmeler ve veri türleri için meta verileri aşağıdaki gibi dışarı aktarabilir:</span><span class="sxs-lookup"><span data-stu-id="94065-103">Svcutil.exe can export metadata for services, contracts, and data types in compiled assemblies, as follows:</span></span>  
  
- <span data-ttu-id="94065-104">Svcutil. exe ' yi kullanarak bir derleme kümesine yönelik tüm derlenmiş hizmet sözleşmeleri için meta verileri dışarı aktarmak için, derlemeleri giriş parametreleri olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="94065-104">To export metadata for all compiled service contracts for a set of assemblies using Svcutil.exe, specify the assemblies as input parameters.</span></span> <span data-ttu-id="94065-105">Bu, varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="94065-105">This is the default behavior.</span></span>  
  
- <span data-ttu-id="94065-106">Svcutil. exe ' yi kullanarak derlenmiş bir hizmetin meta verilerini dışa aktarmak için, hizmet derlemesini veya derlemeleri giriş parametreleri olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="94065-106">To export metadata for a compiled service using Svcutil.exe, specify the service assembly or assemblies as input parameters.</span></span> <span data-ttu-id="94065-107">`/serviceName`Dışarı aktarmak istediğiniz hizmetin yapılandırma adını belirtmek için seçeneğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="94065-107">You must use the `/serviceName` option to indicate the configuration name of the service you want to export.</span></span> <span data-ttu-id="94065-108">Svcutil. exe, belirtilen yürütülebilir derleme için yapılandırma dosyasını otomatik olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="94065-108">Svcutil.exe automatically loads the configuration file for the specified executable assembly.</span></span>  
  
- <span data-ttu-id="94065-109">Bir derleme kümesi içindeki tüm veri anlaşması türlerini dışarı aktarmak için `/dataContractOnly` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="94065-109">To export all data contract types within a set of assemblies, use the `/dataContractOnly` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94065-110">`/reference`Herhangi bir bağımlı derlemeye dosya yollarını belirtmek için seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="94065-110">Use the `/reference` option to specify the file paths to any dependent assemblies.</span></span>  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a><span data-ttu-id="94065-111">Derlenmiş hizmet sözleşmeleri için meta verileri dışarı aktarmak için</span><span class="sxs-lookup"><span data-stu-id="94065-111">To export metadata for compiled service contracts</span></span>  
  
1. <span data-ttu-id="94065-112">Hizmet sözleşmesi uygulamalarınızı bir veya daha fazla sınıf kitaplığı halinde derleyin. 1</span><span class="sxs-lookup"><span data-stu-id="94065-112">Compile your service contract implementations into one or more class libraries.1</span></span>  
  
2. <span data-ttu-id="94065-113">Derlenen derlemelerde Svcutil. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="94065-113">Run Svcutil.exe on the compiled assemblies.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="94065-114">`/reference`Herhangi bir bağımlı derlemeye dosya yolunu belirtmek için anahtarını kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="94065-114">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```console
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a><span data-ttu-id="94065-115">Derlenmiş bir hizmetin meta verilerini dışarı aktarmak için</span><span class="sxs-lookup"><span data-stu-id="94065-115">To export metadata for a compiled service</span></span>  
  
1. <span data-ttu-id="94065-116">Hizmet uygulamanızı yürütülebilir bir derlemede derleyin.</span><span class="sxs-lookup"><span data-stu-id="94065-116">Compile your service implementation into an executable assembly.</span></span>  
  
2. <span data-ttu-id="94065-117">Hizmet yürütülebilir dosyanız için bir yapılandırma dosyası oluşturun ve bir hizmet yapılandırması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="94065-117">Create a configuration file for your service executable and add a service configuration.</span></span>  
  
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
  
3. <span data-ttu-id="94065-118">`/serviceName`Hizmetin yapılandırma adını belirtmek için anahtarı kullanarak derlenmiş hizmet yürütülebilir dosyası üzerinde Svcutil. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="94065-118">Run Svcutil.exe on the compiled service executable using the `/serviceName` switch to specify the configuration name of the service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="94065-119">`/reference`Herhangi bir bağımlı derlemeye dosya yolunu belirtmek için anahtarını kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="94065-119">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```console  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a><span data-ttu-id="94065-120">Derlenen veri sözleşmeleri için meta verileri dışarı aktarmak için</span><span class="sxs-lookup"><span data-stu-id="94065-120">To export metadata for compiled data contracts</span></span>  
  
1. <span data-ttu-id="94065-121">Veri sözleşmesi uygulamalarınızı bir veya daha fazla sınıf kitaplığı halinde derleyin.</span><span class="sxs-lookup"><span data-stu-id="94065-121">Compile your data contract implementations into one or more class libraries.</span></span>  
  
2. <span data-ttu-id="94065-122">`/dataContract`Veri sözleşmelerinin yalnızca meta verilerinin oluşturulması gerektiğini belirtmek için anahtarını kullanarak derlenmiş derlemelerde Svcutil. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="94065-122">Run Svcutil.exe on the compiled assemblies using the `/dataContract` switch to specify that only metadata for data contracts should be generated.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="94065-123">`/reference`Herhangi bir bağımlı derlemeye dosya yolunu belirtmek için anahtarını kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="94065-123">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```console  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a><span data-ttu-id="94065-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="94065-124">Example</span></span>  
 <span data-ttu-id="94065-125">Aşağıdaki örnek, bir basit hizmet uygulama ve yapılandırması için meta verilerin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="94065-125">The following example demonstrates how to generate metadata for a simple service implementation and configuration.</span></span>  
  
 <span data-ttu-id="94065-126">Hizmet sözleşmesinin meta verilerini dışarı aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="94065-126">To export metadata for the service contract.</span></span>  
  
```console  
svcutil.exe Contracts.dll  
```  
  
 <span data-ttu-id="94065-127">Veri sözleşmelerinin meta verilerini dışarı aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="94065-127">To export metadata for the data contracts.</span></span>  
  
```console  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 <span data-ttu-id="94065-128">Hizmet uygulamasının meta verilerini dışarı aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="94065-128">To export metadata for the service implementation.</span></span>  
  
```console  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 <span data-ttu-id="94065-129">, `<path>` Sözleşmelerin. dll yoludur.</span><span class="sxs-lookup"><span data-stu-id="94065-129">The `<path>` is the path to Contracts.dll.</span></span>  
  
```csharp
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
```

```csharp
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
```

```xml  
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
  
## <a name="see-also"></a><span data-ttu-id="94065-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94065-130">See also</span></span>

- [<span data-ttu-id="94065-131">ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="94065-131">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="94065-132">Meta Verileri Dışarı ve İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="94065-132">Exporting and Importing Metadata</span></span>](exporting-and-importing-metadata.md)
