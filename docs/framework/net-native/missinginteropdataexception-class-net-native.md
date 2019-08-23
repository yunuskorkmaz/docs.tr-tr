---
title: MissingInteropDataException Sınıfı (.NET Yerel)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eab4bcf8-9f5f-4731-87d8-842748a6062a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b8d84f8ea9cf8f94cb7a2b155c5d40c6de2979a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941693"
---
# <a name="missinginteropdataexception-class-net-native"></a>MissingInteropDataException Sınıfı (.NET Yerel)
**Windows 10 için Windows uygulamaları için .NET, yalnızca .NET Native**  
  
 Bir el ile sıralama yöntemi çağrıldığında oluşturulan özel durum, ancak bir türün meta verileri statik analiz veya çalışma zamanı yönergeleri dosyasında bulunamamıştır.  
  
 **Uzayına** System. Runtime. CompilerServices  
  
> [!IMPORTANT]
> `MissingInteropDataException` Sınıfı yalnızca .NET Native araç zinciri tarafından dahili kullanıma yöneliktir. Üçüncü taraf kodda kullanılmak üzere değildir veya uygulama kodunuzda özel durumu işlemelisiniz. Bunun yerine, [çalışma zamanı yönergeleri dosyanıza](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)girdiler ekleyerek özel durumu ortadan kaldırabilirsiniz. Daha fazla bilgi için, açıklamalar bölümüne bakın.  
  
## <a name="syntax"></a>Sözdizimi  
 [!code-csharp[ProjectN#21](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missinginteropdataexception_syntax1.cs#21)]
 [!code-vb[ProjectN#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/projectn/vb/missinginteropdataexception_syntax1.vb#21)]  
  
 `MissingInteropDataException` Sınıfı aşağıdaki üyelere sahiptir:  
  
## <a name="constructors"></a>Oluşturucular  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`public MissingInteropDataException(String resourceId, Type pertinentType)`|Hatayı açıklayan ve verileri eksik olan `MissingInteropDataException` türden bir sistem tarafından sağlanan iletinin kimliğini kullanarak sınıfının yeni bir örneğini başlatır. Bu Oluşturucu yalnızca .NET Native araç zinciri tarafından iç kullanım içindir.|  
  
## <a name="properties"></a>Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Özel durum hakkında ek kullanıcı tanımlı bilgiler sağlayan anahtar/değer çiftleri koleksiyonunu alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public string HelpLink { get; set; }`|Bu özel durumla ilişkili Yardım dosyasının bağlantısını alır veya ayarlar. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public int HResult { get; protected set; }`|Belirli bir özel duruma `HRESULT`atanan kodlanmış bir sayısal değer olan öğesini alır veya ayarlar. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public Exception InnerException { get; }`|Geçerli özel duruma neden olan özel durumu alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public string Message { get; }`|Geçerli özel durumu açıklayan bir ileti alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public Type MissingType { get; private set; }`|Verileri eksik olan türü alır veya ayarlar.|  
|`public string Source { get; set; }`|Hataya neden olan uygulamanın veya nesnenin adını alır veya ayarlar. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public string StackTrace { get; }`|Çağrı yığınında anlık çerçevelerin dize gösterimini alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public MethodBase TargetSite { get; }`|Geçerli özel durumu oluşturan yöntemi alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Belirtilen nesnenin geçerli nesneyle eşit olup olmadığını belirler.  (Öğesinden <xref:System.Object>devralındı.)|  
|`protected void Finalize()`|Bir nesnenin çöp toplama tarafından geri alınmadan önce kaynakları serbest bırakma ve diğer temizleme işlemlerini gerçekleştirmesine izin verir. (Öğesinden <xref:System.Object>devralındı.)|  
|`public Exception GetBaseException()`|Bir veya daha fazla sonraki özel durumun asıl nedeni olan özel durumu döndürür. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public int GetHashCode()`|`MissingInteropDataException` Örnek için bir karma kod döndürür.   (Öğesinden <xref:System.Object>devralındı.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Özel durumla <xref:System.Runtime.Serialization.SerializationInfo> ilgili bilgileri içeren bir nesne ayarlar.  (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public Type GetType()`|Geçerli örneğin çalışma zamanı türünü alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`protected Object MemberwiseClone()`|Geçerli nesnenin basit bir kopyasını oluşturur. (Öğesinden <xref:System.Object>devralındı.)|  
|`public string ToString()`|Geçerli özel durumun dize gösterimini döndürür. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
  
## <a name="events"></a>Olaylar  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Özel durum hakkında serileştirilmiş veri içeren bir özel durum nesnesi oluşturmak için bir özel durum serileştirildiğinde gerçekleşir. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
  
## <a name="usage-details"></a>Kullanım ayrıntıları  
 Tür bilgileri kullanılamadığından bir com veya Windows çalışma zamanı bileşenine bir yöntem çağrısı yapılmazsa özeldurumoluşturulur.`MissingInteropDataException`  
  
 Çalışma zamanında bir uygulama için kullanılabilen meta veriler, çalışma zamanı yönergeleri (XML yapılandırma) dosyası, \*. RD. xml tarafından tanımlanır. Uygulamanızın bu özel durumu oluşturmasını engellemek için bu dosyayı, çalışma zamanında bulunması gereken meta verileri tanımlamak üzere değiştirmelisiniz. En yaygın olarak, çalışma zamanı yönergeleri dosyasındaki uygun program `MarshalObject`öğesine `MarshalDelegate`bir, `MarshalStructure` veya özniteliği ekleyerek bu hatayı ele alırsınız. Bu dosyanın biçimi hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
> Bu özel durum, uygulamanız için gereken meta verilerin çalışma zamanında kullanılabilir olmadığını gösterdiği için, bu özel durumu bir `try` / `catch` blokta tutamamalısınız. Bunun yerine, özel durumun nedenini tanılamanıza ve ilgili girişi bir çalışma zamanı yönergeleri dosyasına ekleyerek ortadan kaldırmanız gerekir.  
  
 Sınıfı, başarılı bir yöntem çağrısı için meta verileri `MissingType` gereken türü gösteren tek bir benzersiz üye, özelliği içerir. `MissingInteropDataException` Kalan tüm üyeler temel sınıftan <xref:System.Exception?displayProperty=nameWithType>devralınır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Exception?displayProperty=nameWithType>
- [MissingMetadataException Sınıfı](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
