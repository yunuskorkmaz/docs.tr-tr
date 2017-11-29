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
# <a name="binary-serialization"></a>İkili seri hale getirme

Serileştirme depolama ortamına bir nesne durumunu depolama işlemi olarak tanımlanabilir. Bu işlem sırasında nesnenin genel ve özel alanlar ve sınıfı içeren derlemenin dahil olmak üzere bu sınıfın adını ardından bir veri akışına yazılan bayt akışı dönüştürülür. Nesnenin seri durumdan daha sonra orijinal nesneyi tam bir kopyası oluşturulur.

Seri hale getirme mekanizmasını nesne yönelimli bir ortamda uygularken, kullanım kolaylığı ve esnekliği arasında bileşim sayısı yapmanız gerekir. İşlemin büyük ölçüde otomatik, sağlanan işlem üzerinde yeterli denetim verilir. Örneğin, burada basit ikili serileştirme yeterli değil veya bir sınıf hangi alanları seri hale gerek karar vermek için belirli bir neden olabilir durumlarda gerçekleşebilir. Aşağıdaki bölümlerde .NET ile birlikte sağlanan sağlam seri hale getirme mekanizmasını inceleyin ve bir dizi gereksinimlerinizi karşılamak için işlem özelleştirmenizi önemli özellik vurgulayın.

> [!NOTE]
> Nesnenin serileştirildiği ve farklı .NET Framework sürümleri kullanılarak seri durumdan UTF-8 veya UTF-7 kodlanmış nesne durumunu korunur değil.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

İkili seri hale getirme yapısını özel üyeleri bir nesne ve bu nedenle durumunu değiştirme içinde değiştirilmesine izin verdiği ölçüde ortak API yüzeyi üzerinde çalışan diğer serileştirme çerçeveler JSON.NET gibi önerilir.

## <a name="binary-serialization-in-net-core"></a>.NET Core ikili seri hale getirme

.NET core türlerinin bir kümeyle ikili serileştirme destekler. Desteklenen türlerden birinde listesini görebilir [seri hale getirilebilir türler bölüm](#serializable-types). Türleri tanımlı kümesi .NET Framework 4.5.1 ve sonraki sürümleri ve .NET Core 2.0 ve sonraki sürümler arasında seri hale getirilebilir olması garanti edilir. Mono gibi diğer .NET uygulamaları resmi olarak desteklenmez, ancak aynı zamanda çalışan.

### <a name="serializable-types"></a>Seri hale getirilebilir türler

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
- <xref:System.DBNull?displayProperty=nameWithType>(.NET Core 2.0.2 ve sonraki sürümlerde kullanılabilir)   
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
- <xref:System.ValueTuple?displayProperty=nameWithType>(.NET Framework 4.7 ve önceki sürümlerde getirilemez)  
- <xref:System.ValueType?displayProperty=nameWithType>   
- <xref:System.Version?displayProperty=nameWithType>   
- <xref:System.WeakReference?displayProperty=nameWithType>   
- <xref:System.WeakReference%601?displayProperty=nameWithType>   

## <a name="in-this-section"></a>Bu bölümde

 [Seri hale getirme kavramları](../../../docs/standard/serialization/serialization-concepts.md)  
 Serileştirme olduğu yararlı iki kullanıldığı senaryoları tartışır: zaman kalıcı veri depolama ve geçerken nesneleri uygulama etki alanlarında.  
  
 [Temel seri hale getirme](../../../docs/standard/serialization/basic-serialization.md)  
 İkili kullanın ve nesneleri serileştirmek için biçimlendiricileri SOAP açıklar.  
  
 [Seçmeli seri hale getirme](../../../docs/standard/serialization/selective-serialization.md)  
 Serileştirilmiş öğesinden bir sınıf bazı üyeler önlemek nasıl açıklar.  
  
 [Özel seri hale getirme](../../../docs/standard/serialization/custom-serialization.md)  
 Kullanarak bir sınıf için serileştirme özelleştirmeyi açıklar <xref:System.Runtime.Serialization.ISerializable> arabirimi.  
  
 [Seri hale getirme işlemi adımları](../../../docs/standard/serialization/steps-in-the-serialization-process.md)  
 Kurs açıklayan eylemi serileştirme ne zaman alan <xref:System.Runtime.Serialization.Formatter.Serialize%2A> yöntemi, bir biçimlendirici üzerinde çağrılır.  
  
 [Sürüm dayanıklı seri hale getirme](../../../docs/standard/serialization/version-tolerant-serialization.md)  
 Özel durumlar oluşturan uygulamaların neden olmadan zaman içinde değiştirilebilir serializable türler nasıl oluşturulacağını açıklar.  
  
 [Seri hale getirme yönergeleri](../../../docs/standard/serialization/serialization-guidelines.md)  
 Bir nesneyi serileştirmek ne zaman karar için bazı genel yönergeleri sağlar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Runtime.Serialization>  
 Serileştirme ve seri kaldırma nesneler için kullanılan sınıfları içerir.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [XML ve SOAP seri hale getirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 Ortak dil çalışma zamanı ile içerdiği XML serileştirme mekanizması açıklanmaktadır.  
  
 [Güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md)  
 Serileştirme gerçekleştiren kod yazarken izlemek için güvenli kodlama yönergeleri açıklar.  
  
 [Uzak nesneleri](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58)  
 Çeşitli iletişimleri .NET Framework için kullanılabilecek yöntemleri Uzaktan iletişimler açıklar.  
  
 [ASP.NET ve XML Web hizmeti istemcileri kullanılarak oluşturulan XML Web Hizmetleri](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 Açıklayan ve ASP.NET kullanılarak oluşturulan XML Web Hizmetleri program açıklayan konuları sağlar.
