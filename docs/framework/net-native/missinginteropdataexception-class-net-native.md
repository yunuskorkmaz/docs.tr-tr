---
title: MissingInteropDataException Sınıfı (.NET Yerel)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eab4bcf8-9f5f-4731-87d8-842748a6062a
ms.openlocfilehash: faf14245cd9dd7aa4bf8e89d5a05901279956509
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128274"
---
# <a name="missinginteropdataexception-class-net-native"></a>MissingInteropDataException Sınıfı (.NET Yerel)
**Windows 10 için Windows uygulamaları için .NET, yalnızca .NET Native**  
  
 Bir el ile sıralama yöntemi çağrıldığında oluşturulan özel durum, ancak bir türün meta verileri statik analiz veya çalışma zamanı yönergeleri dosyasında bulunamamıştır.  
  
 **Ad alanı:** System. Runtime. CompilerServices  
  
> [!IMPORTANT]
> `MissingInteropDataException`Sınıfı yalnızca .NET Native araç zinciri tarafından dahili kullanıma yöneliktir. Üçüncü taraf kodda kullanılmak üzere değildir veya uygulama kodunuzda özel durumu işlemelisiniz. Bunun yerine, [çalışma zamanı yönergeleri dosyanıza](runtime-directives-rd-xml-configuration-file-reference.md)girdiler ekleyerek özel durumu ortadan kaldırabilirsiniz. Daha fazla bilgi için, açıklamalar bölümüne bakın.  
  
## <a name="syntax"></a>Sözdizimi  
 [!code-csharp[ProjectN#21](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missinginteropdataexception_syntax1.cs#21)]
 [!code-vb[ProjectN#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/projectn/vb/missinginteropdataexception_syntax1.vb#21)]  
  
 `MissingInteropDataException`Sınıfı aşağıdaki üyelere sahiptir:  
  
## <a name="constructors"></a>Oluşturucular  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`public MissingInteropDataException(String resourceId, Type pertinentType)`|`MissingInteropDataException`Hatayı açıklayan ve verileri eksik olan türden bir sistem tarafından sağlanan ILETININ kimliğini kullanarak sınıfının yeni bir örneğini başlatır. Bu Oluşturucu yalnızca .NET Native araç zinciri tarafından iç kullanım içindir.|  
  
## <a name="properties"></a>Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Özel durum hakkında ek kullanıcı tanımlı bilgiler sağlayan anahtar/değer çiftleri koleksiyonunu alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public string HelpLink { get; set; }`|Bu özel durumla ilişkili Yardım dosyasının bağlantısını alır veya ayarlar. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public int HResult { get; protected set; }`|`HRESULT`Belirli bir özel duruma atanan kodlanmış bir sayısal değer olan öğesini alır veya ayarlar. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public Exception InnerException { get; }`|Geçerli özel duruma neden olan özel durumu alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public string Message { get; }`|Geçerli özel durumu açıklayan bir ileti alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public Type MissingType { get; private set; }`|Verileri eksik olan türü alır veya ayarlar.|  
|`public string Source { get; set; }`|Hataya neden olan uygulamanın veya nesnenin adını alır veya ayarlar. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public string StackTrace { get; }`|Çağrı yığınında anlık çerçevelerin dize gösterimini alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public MethodBase TargetSite { get; }`|Geçerli özel durumu oluşturan yöntemi alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Belirtilen nesnenin geçerli nesneye eşit olup olmadığını belirler.  (Öğesinden devralındı <xref:System.Object> .)|  
|`protected void Finalize()`|Bir nesnenin çöp toplama tarafından geri alınmadan önce kaynakları serbest bırakma ve diğer temizleme işlemlerini gerçekleştirmesine izin verir. (Öğesinden devralındı <xref:System.Object> .)|  
|`public Exception GetBaseException()`|Bir veya daha fazla sonraki özel durumun asıl nedeni olan özel durumu döndürür. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public int GetHashCode()`|Örnek için bir karma kod döndürür `MissingInteropDataException` .   (Öğesinden devralındı <xref:System.Object> .)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|<xref:System.Runtime.Serialization.SerializationInfo>Özel durumla ilgili bilgileri içeren bir nesne ayarlar.  (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public Type GetType()`|Geçerli örneğin çalışma zamanı türünü alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`protected Object MemberwiseClone()`|Geçerli nesnenin basit bir kopyasını oluşturur. (Öğesinden devralındı <xref:System.Object> .)|  
|`public string ToString()`|Geçerli özel durumun dize gösterimini döndürür. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
  
## <a name="events"></a>Olaylar  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Özel durum hakkında serileştirilmiş veri içeren bir özel durum nesnesi oluşturmak için bir özel durum serileştirildiğinde gerçekleşir. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
  
## <a name="usage-details"></a>Kullanım Ayrıntıları  
 `MissingInteropDataException`Tür bilgileri kullanılamadığından BIR com veya Windows çalışma zamanı bileşenine bir yöntem çağrısı yapılmazsa özel durum oluşturulur.  
  
 Çalışma zamanında bir uygulama için kullanılabilen meta veriler, çalışma zamanı yönergeleri (XML yapılandırma) dosyası, \* . RD. xml tarafından tanımlanır. Uygulamanızın bu özel durumu oluşturmasını engellemek için bu dosyayı, çalışma zamanında bulunması gereken meta verileri tanımlamak üzere değiştirmelisiniz. En yaygın olarak, `MarshalObject` `MarshalDelegate` `MarshalStructure` çalışma zamanı yönergeleri dosyasındaki uygun program öğesine bir, veya özniteliği ekleyerek bu hatayı ele alırsınız. Bu dosyanın biçimi hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
> Bu özel durum, uygulamanız için gereken meta verilerin çalışma zamanında kullanılabilir olmadığını gösterdiği için, bu özel durumu bir blokta tutamamalısınız `try` / `catch` . Bunun yerine, özel durumun nedenini tanılamanıza ve ilgili girişi bir çalışma zamanı yönergeleri dosyasına ekleyerek ortadan kaldırmanız gerekir.  
  
 `MissingInteropDataException`Sınıfı, `MissingType` başarılı bir yöntem çağrısı için meta verileri gereken türü gösteren tek bir benzersiz üye, özelliği içerir. Kalan tüm üyeler temel sınıftan devralınır <xref:System.Exception?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Exception?displayProperty=nameWithType>
- [MissingMetadataException Sınıfı](missingmetadataexception-class-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
