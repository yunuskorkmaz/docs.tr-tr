---
title: "SerializationBinder ile Seri Hale Getirme ve Seri Durumdan Çıkarmayı Denetleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba2140459c0b571e9b35824d3dba274e8447ac40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a><span data-ttu-id="7025d-102">SerializationBinder ile Seri Hale Getirme ve Seri Durumdan Çıkarmayı Denetleme</span><span class="sxs-lookup"><span data-stu-id="7025d-102">Controlling Serialization and Deserialization with SerializationBinder</span></span>
<span data-ttu-id="7025d-103">Serileştirme sırasında bir biçimlendirici doğru türü ve sürümü bir nesne örneğini oluşturmak için gereken bilgileri iletir.</span><span class="sxs-lookup"><span data-stu-id="7025d-103">During serialization, a formatter transmits the information required to create an instance of an object of the correct type and version.</span></span> <span data-ttu-id="7025d-104">Bu bilgiler genelde derleme nesnesinin adını ve tam tür adını içerir.</span><span class="sxs-lookup"><span data-stu-id="7025d-104">This information generally includes the full type name and assembly name of the object.</span></span> <span data-ttu-id="7025d-105">Varsayılan olarak, seri durumdan çıkarma aynı nesne örneğini oluşturmak için bu bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="7025d-105">By default, deserialization uses this information to create an instance of an identical object.</span></span> <span data-ttu-id="7025d-106">Bazı kullanıcılar, hangi sınıfının seri hale getirmek ve seri durumdan çıkarma gerçekleştirme makinede özgün sınıfı olmayabilir için ya da seri durumdan kontrol gerekebilir, özgün sınıf derlemeler arasında taşınmış veya sınıf farklı bir sürümü gerekiyor. Sunucu ve istemci.</span><span class="sxs-lookup"><span data-stu-id="7025d-106">Some users may need to control which class to serialize and deserialize, either because the original class may not exist on the machine performing deserialization, the original class has moved between assemblies, or a different version of the class is required on the server and client.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="7025d-107">[Seri hale getirme Bağlayıcısı kullanımı](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).</span><span class="sxs-lookup"><span data-stu-id="7025d-107"> [Usage of Serialization Binder](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="7025d-108">Bu işlevsellik yalnızca kullanırken kullanılabilir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> veya <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7025d-108">This functionality is only available when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or the <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span>  
  
## <a name="using-serializationbinder"></a><span data-ttu-id="7025d-109">SerializationBinder kullanma</span><span class="sxs-lookup"><span data-stu-id="7025d-109">Using SerializationBinder</span></span>  
 <span data-ttu-id="7025d-110"><xref:System.Runtime.Serialization.SerializationBinder>bir Özet sınıf, seri hale getirme ve seri durumdan çıkarma sırasında kullanılan gerçek türlerini denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7025d-110"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="7025d-111">Serileştirme ve seri durumundan çıkarma sırasında kullanılan türlerini denetlemek için öğesinden bir sınıf türetin <xref:System.Runtime.Serialization.SerializationBinder> ve geçersiz kılma <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> ve <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="7025d-111">To control the types used during serialization and deserialization, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> methods.</span></span> <span data-ttu-id="7025d-112"><xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> Metodu bir <xref:System.Type> ve bir derleme ve tür adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7025d-112">The <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> method takes a <xref:System.Type> and returns an assembly and type name.</span></span> <span data-ttu-id="7025d-113"><xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> Yöntemi bir derleme ve tür adını alır ve döndüren bir <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="7025d-113">The <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> method takes an assembly and type name and returns a <xref:System.Type>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7025d-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7025d-114">See Also</span></span>  
 [<span data-ttu-id="7025d-115">Serileştirme ve Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="7025d-115">Serialization and Deserialization</span></span>](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [<span data-ttu-id="7025d-116">Serileştirme Bağlayıcısı Kullanımı</span><span class="sxs-lookup"><span data-stu-id="7025d-116">Usage of Serialization Binder</span></span>](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
