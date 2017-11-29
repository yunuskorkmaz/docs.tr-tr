---
title: "İkili seri hale getirme"
ms.date: 08/11/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
caps.latest.revision: "5"
author: ViktorHofer
ms.author: mairaw
ms.openlocfilehash: 74ee4e21934c1e4f3fd008664b1315429dc47b37
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="binary-serialization"></a><span data-ttu-id="3a259-102">İkili seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="3a259-102">Binary serialization</span></span>

<span data-ttu-id="3a259-103">Serileştirme depolama ortamına bir nesne durumunu depolama işlemi olarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3a259-103">Serialization can be defined as the process of storing the state of an object to a storage medium.</span></span> <span data-ttu-id="3a259-104">Bu işlem sırasında nesnenin genel ve özel alanlar ve sınıfı içeren derlemenin dahil olmak üzere bu sınıfın adını ardından bir veri akışına yazılan bayt akışı dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="3a259-104">During this process, the public and private fields of the object and the name of the class, including the assembly containing the class, are converted to a stream of bytes, which is then written to a data stream.</span></span> <span data-ttu-id="3a259-105">Nesnenin seri durumdan daha sonra orijinal nesneyi tam bir kopyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3a259-105">When the object is subsequently deserialized, an exact clone of the original object is created.</span></span>

<span data-ttu-id="3a259-106">Seri hale getirme mekanizmasını nesne yönelimli bir ortamda uygularken, kullanım kolaylığı ve esnekliği arasında bileşim sayısı yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a259-106">When implementing a serialization mechanism in an object-oriented environment, you have to make a number of tradeoffs between ease of use and flexibility.</span></span> <span data-ttu-id="3a259-107">İşlemin büyük ölçüde otomatik, sağlanan işlem üzerinde yeterli denetim verilir.</span><span class="sxs-lookup"><span data-stu-id="3a259-107">The process can be automated to a large extent, provided you are given sufficient control over the process.</span></span> <span data-ttu-id="3a259-108">Örneğin, burada basit ikili serileştirme yeterli değil veya bir sınıf hangi alanları seri hale gerek karar vermek için belirli bir neden olabilir durumlarda gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="3a259-108">For example, situations may arise where simple binary serialization is not sufficient, or there might be a specific reason to decide which fields in a class need to be serialized.</span></span> <span data-ttu-id="3a259-109">Aşağıdaki bölümlerde .NET ile birlikte sağlanan sağlam seri hale getirme mekanizmasını inceleyin ve bir dizi gereksinimlerinizi karşılamak için işlem özelleştirmenizi önemli özellik vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="3a259-109">The following sections examine the robust serialization mechanism provided with .NET and highlight a number of important features that allow you to customize the process to meet your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="3a259-110">Nesnenin serileştirildiği ve farklı .NET Framework sürümleri kullanılarak seri durumdan UTF-8 veya UTF-7 kodlanmış nesne durumunu korunur değil.</span><span class="sxs-lookup"><span data-stu-id="3a259-110">The state of a UTF-8 or UTF-7 encoded object is not preserved if the object is serialized and deserialized using different .NET Framework versions.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="3a259-111">İkili seri hale getirme yapısını özel üyeleri bir nesne ve bu nedenle durumunu değiştirme içinde değiştirilmesine izin verdiği ölçüde ortak API yüzeyi üzerinde çalışan diğer serileştirme çerçeveler JSON.NET gibi önerilir.</span><span class="sxs-lookup"><span data-stu-id="3a259-111">As the nature of binary serialization allows the modification of private members inside an object and therefore changing the state of it, other serialization frameworks like JSON.NET which operate on the public API surface are recommended.</span></span>

## <a name="binary-serialization-in-net-core"></a><span data-ttu-id="3a259-112">.NET Core ikili seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="3a259-112">Binary serialization in .NET Core</span></span>

<span data-ttu-id="3a259-113">.NET core türlerinin bir kümeyle ikili serileştirme destekler.</span><span class="sxs-lookup"><span data-stu-id="3a259-113">.NET Core supports binary serialization with a subset of types.</span></span> <span data-ttu-id="3a259-114">Desteklenen türlerden birinde listesini görebilir [seri hale getirilebilir türler bölüm](#serializable-types).</span><span class="sxs-lookup"><span data-stu-id="3a259-114">You can see the list of supported types in the [Serializable types section](#serializable-types).</span></span> <span data-ttu-id="3a259-115">Türleri tanımlı kümesi .NET Framework 4.5.1 ve sonraki sürümleri ve .NET Core 2.0 ve sonraki sürümler arasında seri hale getirilebilir olması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="3a259-115">The defined set of types are guaranteed to be serializable between .NET Framework 4.5.1 and later versions and .NET Core 2.0 and later versions.</span></span> <span data-ttu-id="3a259-116">Mono gibi diğer .NET uygulamaları resmi olarak desteklenmez, ancak aynı zamanda çalışan.</span><span class="sxs-lookup"><span data-stu-id="3a259-116">Other .NET implementations, such as Mono, aren't officially supported but should also be working.</span></span>

### <a name="serializable-types"></a><span data-ttu-id="3a259-117">Seri hale getirilebilir türler</span><span class="sxs-lookup"><span data-stu-id="3a259-117">Serializable types</span></span>

- <xref:System.AggregateException?displayProperty=nameWithType>   
- <xref:System.Array?displayProperty=nameWithType>   
- <xref:System.ArraySegment%601?displayProperty=nameWithType>   
- <xref:System.Attribute?displayProperty=nameWithType>   
- <xref:System.Boolean?displayProperty=nameWithType>   
- <xref:System.Byte?displayProperty=nameWithType>   
- <xref:System.Char?displayProperty=nameWithType>   
- <xref:System.Collections.ArrayList?displayProperty=nameWithType>   
- <xref:System.Collections.BitArray?displayProperty=nameWithType>   
- <xref:System.Collections.Comparer?displayProperty=nameWithType>   
- <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType>   
- <xref:System.Collections.Hashtable?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.Queue?displayProperty=nameWithType>   
- <xref:System.Collections.SortedList?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Stack?displayProperty=nameWithType>   
- <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType>   
- <span data-ttu-id="3a259-118"><xref:System.DBNull?displayProperty=nameWithType>(.NET Core 2.0.2 ve sonraki sürümlerde kullanılabilir)</span><span class="sxs-lookup"><span data-stu-id="3a259-118"><xref:System.DBNull?displayProperty=nameWithType> (available in .NET Core 2.0.2 and later versions)</span></span>   
- <xref:System.Data.DataSet?displayProperty=nameWithType>   
- <xref:System.Data.DataTable?displayProperty=nameWithType>   
- <xref:System.Data.PropertyCollection?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType>   
- <xref:System.DateTime?displayProperty=nameWithType>   
- <xref:System.DateTimeOffset?displayProperty=nameWithType>   
- <xref:System.Decimal?displayProperty=nameWithType>   
- <xref:System.Double?displayProperty=nameWithType>   
- <xref:System.Drawing.Color?displayProperty=nameWithType>   
- <xref:System.Drawing.Point?displayProperty=nameWithType>   
- <xref:System.Drawing.PointF?displayProperty=nameWithType>   
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>   
- <xref:System.Drawing.RectangleF?displayProperty=nameWithType>   
- <xref:System.Drawing.Size?displayProperty=nameWithType>   
- <xref:System.Drawing.SizeF?displayProperty=nameWithType>   
- <xref:System.Enum?displayProperty=nameWithType>   
- <xref:System.Exception?displayProperty=nameWithType>   
- <xref:System.Globalization.CompareInfo?displayProperty=nameWithType>   
- <xref:System.Globalization.SortVersion?displayProperty=nameWithType>   
- <xref:System.Guid?displayProperty=nameWithType>   
- <xref:System.Int16?displayProperty=nameWithType>   
- <xref:System.Int32?displayProperty=nameWithType>   
- <xref:System.Int64?displayProperty=nameWithType>   
- <xref:System.IntPtr?displayProperty=nameWithType>   
- <xref:System.Net.Cookie?displayProperty=nameWithType>   
- <xref:System.Net.CookieCollection?displayProperty=nameWithType>   
- <xref:System.Net.CookieContainer?displayProperty=nameWithType>   
- <xref:System.Nullable%601?displayProperty=nameWithType>   
- <xref:System.Numerics.BigInteger?displayProperty=nameWithType>   
- <xref:System.Numerics.Complex?displayProperty=nameWithType>   
- <xref:System.Object?displayProperty=nameWithType>   
- <xref:System.SByte?displayProperty=nameWithType>   
- <xref:System.Single?displayProperty=nameWithType>   
- <xref:System.String?displayProperty=nameWithType>   
- <xref:System.StringComparer?displayProperty=nameWithType>   
- <xref:System.Text.StringBuilder?displayProperty=nameWithType>   
- <xref:System.TimeSpan?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType>   
- <xref:System.Tuple?displayProperty=nameWithType>   
- <xref:System.UInt16?displayProperty=nameWithType>   
- <xref:System.UInt32?displayProperty=nameWithType>   
- <xref:System.UInt64?displayProperty=nameWithType>   
- <xref:System.UIntPtr?displayProperty=nameWithType>   
- <xref:System.Uri?displayProperty=nameWithType>   
- <span data-ttu-id="3a259-119"><xref:System.ValueTuple?displayProperty=nameWithType>(.NET Framework 4.7 ve önceki sürümlerde getirilemez)</span><span class="sxs-lookup"><span data-stu-id="3a259-119"><xref:System.ValueTuple?displayProperty=nameWithType> (not serializable in .NET Framework 4.7 and earlier versions)</span></span>  
- <xref:System.ValueType?displayProperty=nameWithType>   
- <xref:System.Version?displayProperty=nameWithType>   
- <xref:System.WeakReference?displayProperty=nameWithType>   
- <xref:System.WeakReference%601?displayProperty=nameWithType>   

## <a name="in-this-section"></a><span data-ttu-id="3a259-120">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="3a259-120">In this section</span></span>

 [<span data-ttu-id="3a259-121">Seri hale getirme kavramları</span><span class="sxs-lookup"><span data-stu-id="3a259-121">Serialization Concepts</span></span>](../../../docs/standard/serialization/serialization-concepts.md)  
 <span data-ttu-id="3a259-122">Serileştirme olduğu yararlı iki kullanıldığı senaryoları tartışır: zaman kalıcı veri depolama ve geçerken nesneleri uygulama etki alanlarında.</span><span class="sxs-lookup"><span data-stu-id="3a259-122">Discusses two scenarios where serialization is useful: when persisting data to storage and when passing objects across application domains.</span></span>  
  
 [<span data-ttu-id="3a259-123">Temel seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="3a259-123">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
 <span data-ttu-id="3a259-124">İkili kullanın ve nesneleri serileştirmek için biçimlendiricileri SOAP açıklar.</span><span class="sxs-lookup"><span data-stu-id="3a259-124">Describes how to use the binary and SOAP formatters to serialize objects.</span></span>  
  
 [<span data-ttu-id="3a259-125">Seçmeli seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="3a259-125">Selective Serialization</span></span>](../../../docs/standard/serialization/selective-serialization.md)  
 <span data-ttu-id="3a259-126">Serileştirilmiş öğesinden bir sınıf bazı üyeler önlemek nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="3a259-126">Describes how to prevent some members of a class from being serialized.</span></span>  
  
 [<span data-ttu-id="3a259-127">Özel seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="3a259-127">Custom Serialization</span></span>](../../../docs/standard/serialization/custom-serialization.md)  
 <span data-ttu-id="3a259-128">Kullanarak bir sınıf için serileştirme özelleştirmeyi açıklar <xref:System.Runtime.Serialization.ISerializable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3a259-128">Describes how to customize serialization for a class by using the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 [<span data-ttu-id="3a259-129">Seri hale getirme işlemi adımları</span><span class="sxs-lookup"><span data-stu-id="3a259-129">Steps in the Serialization Process</span></span>](../../../docs/standard/serialization/steps-in-the-serialization-process.md)  
 <span data-ttu-id="3a259-130">Kurs açıklayan eylemi serileştirme ne zaman alan <xref:System.Runtime.Serialization.Formatter.Serialize%2A> yöntemi, bir biçimlendirici üzerinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3a259-130">Describes the course of action serialization takes when the <xref:System.Runtime.Serialization.Formatter.Serialize%2A> method is called on a formatter.</span></span>  
  
 [<span data-ttu-id="3a259-131">Sürüm dayanıklı seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="3a259-131">Version Tolerant Serialization</span></span>](../../../docs/standard/serialization/version-tolerant-serialization.md)  
 <span data-ttu-id="3a259-132">Özel durumlar oluşturan uygulamaların neden olmadan zaman içinde değiştirilebilir serializable türler nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="3a259-132">Explains how to create serializable types that can be modified over time without causing applications to throw exceptions.</span></span>  
  
 [<span data-ttu-id="3a259-133">Seri hale getirme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="3a259-133">Serialization Guidelines</span></span>](../../../docs/standard/serialization/serialization-guidelines.md)  
 <span data-ttu-id="3a259-134">Bir nesneyi serileştirmek ne zaman karar için bazı genel yönergeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a259-134">Provides some general guidelines for deciding when to serialize an object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3a259-135">Başvuru</span><span class="sxs-lookup"><span data-stu-id="3a259-135">Reference</span></span>  
 <xref:System.Runtime.Serialization>  
 <span data-ttu-id="3a259-136">Serileştirme ve seri kaldırma nesneler için kullanılan sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="3a259-136">Contains classes that can be used for serializing and deserializing objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3a259-137">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="3a259-137">Related sections</span></span>  
 [<span data-ttu-id="3a259-138">XML ve SOAP seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="3a259-138">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 <span data-ttu-id="3a259-139">Ortak dil çalışma zamanı ile içerdiği XML serileştirme mekanizması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a259-139">Describes the XML serialization mechanism that is included with the common language runtime.</span></span>  
  
 [<span data-ttu-id="3a259-140">Güvenlik ve Serileştirme</span><span class="sxs-lookup"><span data-stu-id="3a259-140">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)  
 <span data-ttu-id="3a259-141">Serileştirme gerçekleştiren kod yazarken izlemek için güvenli kodlama yönergeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="3a259-141">Describes the secure coding guidelines to follow when writing code that performs serialization.</span></span>  
  
 [<span data-ttu-id="3a259-142">Uzak nesneleri</span><span class="sxs-lookup"><span data-stu-id="3a259-142">Remote Objects</span></span>](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58)  
 <span data-ttu-id="3a259-143">Çeşitli iletişimleri .NET Framework için kullanılabilecek yöntemleri Uzaktan iletişimler açıklar.</span><span class="sxs-lookup"><span data-stu-id="3a259-143">Describes the various communications methods available in the .NET Framework for remote communications.</span></span>  
  
 [<span data-ttu-id="3a259-144">ASP.NET ve XML Web hizmeti istemcileri kullanılarak oluşturulan XML Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="3a259-144">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 <span data-ttu-id="3a259-145">Açıklayan ve ASP.NET kullanılarak oluşturulan XML Web Hizmetleri program açıklayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a259-145">Provides topics that describe and explain how to program XML Web services created using ASP.NET.</span></span>
