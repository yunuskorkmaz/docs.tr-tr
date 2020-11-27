---
title: 'Azaltma: Uygulama Etki Alanlarında Nesneleri Seri Durumdan Çıkarma'
description: Uygulama etki alanları genelinde mantıksal çağrı bağlamındaki nesneleri seri durumdan çıkarma girişiminin özel durum oluşturduğu bir sorunu tanılamayı ve hafifletmek hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
ms.openlocfilehash: 1b8060870962ddd26d90c4152a270a65936c2af3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256644"
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a><span data-ttu-id="82fbc-103">Azaltma: Uygulama Etki Alanlarında Nesneleri Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="82fbc-103">Mitigation: Deserialization of Objects Across App Domains</span></span>

<span data-ttu-id="82fbc-104">Bazı durumlarda, bir uygulama farklı uygulama temeli kullanan iki veya daha fazla uygulama etki alanı kullandığında, uygulama etki alanları arasında nesnelerin mantıksal çağrı bağlamında serisini kaldırma girişimi özel bir durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="82fbc-104">In some cases, when an app uses two or more app domains with different application bases, the attempt to deserialize objects in the logical call context across app domains throws an exception.</span></span>  
  
## <a name="diagnosing-the-issue"></a><span data-ttu-id="82fbc-105">Sorunu tanılama</span><span class="sxs-lookup"><span data-stu-id="82fbc-105">Diagnosing the issue</span></span>  

 <span data-ttu-id="82fbc-106">Sorun, sırasıyla aşağıdaki koşullar altında ortaya çıkar:</span><span class="sxs-lookup"><span data-stu-id="82fbc-106">The issue arises under the following sequence of conditions:</span></span>  
  
1. <span data-ttu-id="82fbc-107">Bir uygulama, farklı uygulama temel dizini kullanan iki veya daha fazla uygulama etki alanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="82fbc-107">An app uses two or more app domains with different application bases.</span></span>  
  
2. <span data-ttu-id="82fbc-108">Bazı türler, <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> veya <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> gibi bir yöntem çağrılarak açıkça <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType> içine eklenir.</span><span class="sxs-lookup"><span data-stu-id="82fbc-108">Some types are explicitly added to the <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> by calling a method such as <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> or <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="82fbc-109">Bu türler seri hale getirilebilir olarak işaretlenmez ve genel bütünleştirilmiş derleme önbelleği içinde saklanmaz.</span><span class="sxs-lookup"><span data-stu-id="82fbc-109">These types are not marked as serializable and are not stored in the global assembly cache.</span></span>  
  
3. <span data-ttu-id="82fbc-110">Daha sonra, varsayılan olmayan uygulama etki alanında çalışan kod, bir yapılandırma dosyasından değer okumayı veya bir nesnenin serisini kaldırmak için XML kullanmayı dener.</span><span class="sxs-lookup"><span data-stu-id="82fbc-110">Later, code running in the non-default app domain tries to read a value from a configuration file or use XML to deserialize an object.</span></span>  
  
4. <span data-ttu-id="82fbc-111">Bir yapılandırma dosyasından okumak veya nesnenin serisini kaldırmak için, bir <xref:System.Xml.XmlReader> nesnesi yapılandırma sistemine erişmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="82fbc-111">In order to read from a configuration file or deserialize the object, an <xref:System.Xml.XmlReader> object tries to access the configuration system.</span></span>  
  
5. <span data-ttu-id="82fbc-112">Eğer yapılandırma sistemi daha başlatılmadıysa, başlatılmasını tamamlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="82fbc-112">If the configuration system has not already been initialized, it must complete its initialization.</span></span> <span data-ttu-id="82fbc-113">Bu, diğer şeylerin yanı sıra, çalışma zamanının bir yapılandırma sistemi için tutarlı bir yol oluşturması gerektiği anlamına gelir ki bunu aşağıdaki şekilde gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="82fbc-113">This means, among other things, that the runtime has to create a stable path for a configuration system, which it does as follows:</span></span>  
  
    1. <span data-ttu-id="82fbc-114">Varsayılan olmayan uygulama etki alanı için kanıt arar.</span><span class="sxs-lookup"><span data-stu-id="82fbc-114">It looks for evidence for the non-default app domain.</span></span>  
  
    2. <span data-ttu-id="82fbc-115">Varsayılan uygulama etki alanını temel alarak, varsayılan olmayan etki alanı için olan kanıtları hesaplamayı dener.</span><span class="sxs-lookup"><span data-stu-id="82fbc-115">It tries to calculate the evidence for the non-default app domain based on the default app domain.</span></span>  
  
    3. <span data-ttu-id="82fbc-116">Varsayılan uygulama etki alanı için kanıt alma çağrısı, varsayılan olmayan uygulama etki alanından varsayılan uygulama etki alanına, uygulama etki alanları arasında bir çağrıyı tetikler.</span><span class="sxs-lookup"><span data-stu-id="82fbc-116">The call to get evidence for the default app domain triggers a cross-app domain call from the non-default app domain to the default app domain.</span></span>  
  
    4. <span data-ttu-id="82fbc-117">.NET Framework'teki uygulama etki alanları arası anlaşması kapsamında, mantıksal çağrı bağlamının içeriğinin uygulama etki alanı sınırları arasında sıralanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="82fbc-117">As part of the cross-app domain contract in the .NET Framework, the contents of the logical call context also have to be marshaled across app domain boundaries.</span></span>  
  
6. <span data-ttu-id="82fbc-118">Mantıksal çağrı bağlamındaki türler varsayılan uygulama etki alanında çözümlenemediği için, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="82fbc-118">Because the types that are in the logical call context cannot be resolved in the default app domain, an exception is thrown.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="82fbc-119">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="82fbc-119">Mitigation</span></span>  

 <span data-ttu-id="82fbc-120">Bu sorunun geçici çözümü için, aşağıdakini yapın</span><span class="sxs-lookup"><span data-stu-id="82fbc-120">To work around this issue, do the following</span></span>  
  
1. <span data-ttu-id="82fbc-121">Özel durumun oluşturulduğu çağrı yığınındaki `get_Evidence` çağrısını bulun.</span><span class="sxs-lookup"><span data-stu-id="82fbc-121">Look for the call to `get_Evidence` in the call stack when the exception is thrown.</span></span> <span data-ttu-id="82fbc-122">Özel durum, <xref:System.IO.FileNotFoundException> ve <xref:System.Runtime.Serialization.SerializationException> dahil birçok özel durumun ait olduğu büyük bir alt kümedeki özel durumlardan herhangi biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="82fbc-122">The exception can be any of a large subset of exceptions, including <xref:System.IO.FileNotFoundException> and <xref:System.Runtime.Serialization.SerializationException>.</span></span>  
  
2. <span data-ttu-id="82fbc-123">Uygulamada mantıksal çağrı bağlamına hiçbir nesnenin eklenmediği yeri bulun ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="82fbc-123">Identify the place in the app where no objects are added to the logical call context and add the following code:</span></span>  
  
    ```csharp
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```
  
## <a name="see-also"></a><span data-ttu-id="82fbc-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82fbc-124">See also</span></span>

- [<span data-ttu-id="82fbc-125">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="82fbc-125">Application compatibility</span></span>](application-compatibility.md)
