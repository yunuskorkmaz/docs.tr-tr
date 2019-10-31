---
title: MissingInteropDataException Sınıfı (.NET Yerel)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eab4bcf8-9f5f-4731-87d8-842748a6062a
ms.openlocfilehash: faf14245cd9dd7aa4bf8e89d5a05901279956509
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128274"
---
# <a name="missinginteropdataexception-class-net-native"></a>MissingInteropDataException Sınıfı (.NET Yerel)
**Windows 10 için Windows uygulamaları için .NET, yalnızca .NET Native**  
  
 Bir el ile sıralama yöntemi çağrıldığında oluşturulan özel durum, ancak bir türün meta verileri statik analiz veya çalışma zamanı yönergeleri dosyasında bulunamamıştır.  
  
 **Ad alanı:** System. Runtime. CompilerServices  
  
> [!IMPORTANT]
> `MissingInteropDataException` sınıfı, yalnızca .NET Native araç zinciri tarafından dahili kullanıma yöneliktir. Üçüncü taraf kodda kullanılmak üzere değildir veya uygulama kodunuzda özel durumu işlemelisiniz. Bunun yerine, [çalışma zamanı yönergeleri dosyanıza](runtime-directives-rd-xml-configuration-file-reference.md)girdiler ekleyerek özel durumu ortadan kaldırabilirsiniz. Daha fazla bilgi için, açıklamalar bölümüne bakın.  
  
## <a name="syntax"></a>Sözdizimi  
 [!code-csharp[ProjectN#21](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missinginteropdataexception_syntax1.cs#21)]
 [!code-vb[ProjectN#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/projectn/vb/missinginteropdataexception_syntax1.vb#21)]  
  
 `MissingInteropDataException` sınıfı aşağıdaki üyelere sahiptir:  
  
## <a name="constructors"></a>Oluşturucular  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`public MissingInteropDataException(String resourceId, Type pertinentType)`|Hatayı açıklayan ve verileri eksik olan türden bir sistem tarafından sağlanan iletinin KIMLIĞINI kullanarak `MissingInteropDataException` sınıfının yeni bir örneğini başlatır. Bu Oluşturucu yalnızca .NET Native araç zinciri tarafından iç kullanım içindir.|  
  
## <a name="properties"></a>Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Özel durum hakkında ek kullanıcı tanımlı bilgiler sağlayan anahtar/değer çiftleri koleksiyonunu alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public string HelpLink { get; set; }`|Bu özel durumla ilişkili Yardım dosyasının bağlantısını alır veya ayarlar. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public int HResult { get; protected set; }`|Belirli bir özel duruma atanan kodlanmış sayısal değer olan `HRESULT`alır veya ayarlar. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public Exception InnerException { get; }`|Geçerli özel duruma neden olan özel durumu alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public string Message { get; }`|Geçerli özel durumu açıklayan bir ileti alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public Type MissingType { get; private set; }`|Verileri eksik olan türü alır veya ayarlar.|  
|`public string Source { get; set; }`|Hataya neden olan uygulamanın veya nesnenin adını alır veya ayarlar. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public string StackTrace { get; }`|Çağrı yığınında anlık çerçevelerin dize gösterimini alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public MethodBase TargetSite { get; }`|Geçerli özel durumu oluşturan yöntemi alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Belirtilen nesnenin geçerli nesneyle eşit olup olmadığını belirler.  (<xref:System.Object>devralındı.)|  
|`protected void Finalize()`|Bir nesnenin çöp toplama tarafından geri alınmadan önce kaynakları serbest bırakma ve diğer temizleme işlemlerini gerçekleştirmesine izin verir. (<xref:System.Object>devralındı.)|  
|`public Exception GetBaseException()`|Bir veya daha fazla sonraki özel durumun asıl nedeni olan özel durumu döndürür. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public int GetHashCode()`|`MissingInteropDataException` örneği için bir karma kod döndürür.   (<xref:System.Object>devralındı.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Özel durum hakkında bilgi içeren bir <xref:System.Runtime.Serialization.SerializationInfo> nesnesi ayarlar.  (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public Type GetType()`|Geçerli örneğin çalışma zamanı türünü alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`protected Object MemberwiseClone()`|Geçerli nesnenin basit bir kopyasını oluşturur. (<xref:System.Object>devralındı.)|  
|`public string ToString()`|Geçerli özel durumun dize gösterimini döndürür. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
  
## <a name="events"></a>Olaylar  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Özel durum hakkında serileştirilmiş veri içeren bir özel durum nesnesi oluşturmak için bir özel durum serileştirildiğinde gerçekleşir. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
  
## <a name="usage-details"></a>Kullanım ayrıntıları  
 Tür bilgileri kullanılamadığından bir COM veya Windows Çalışma Zamanı bileşenine bir yöntem çağrısı yapılmazsa `MissingInteropDataException` özel durumu oluşturulur.  
  
 Çalışma zamanında bir uygulama için kullanılabilen meta veriler, \*. RD. xml çalışma zamanı yönergeleri (XML yapılandırma) dosyası tarafından tanımlanır. Uygulamanızın bu özel durumu oluşturmasını engellemek için bu dosyayı, çalışma zamanında bulunması gereken meta verileri tanımlamak üzere değiştirmelisiniz. En yaygın olarak, çalışma zamanı yönergeleri dosyasındaki uygun program öğesine bir `MarshalObject`, `MarshalDelegate`veya `MarshalStructure` özniteliği ekleyerek bu hatayı ele alırsınız. Bu dosyanın biçimi hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
> Bu özel durum, uygulamanız için gereken meta verilerin çalışma zamanında kullanılabilir olmadığını gösterdiği için, bu özel durumu bir `try`/`catch` bloğunda tutamamalısınız. Bunun yerine, özel durumun nedenini tanılamanıza ve ilgili girişi bir çalışma zamanı yönergeleri dosyasına ekleyerek ortadan kaldırmanız gerekir.  
  
 `MissingInteropDataException` sınıfı, başarılı bir yöntem çağrısı için meta verileri gerekli olan türü belirten, `MissingType` özelliği olan tek bir benzersiz üye içerir. Kalan tüm Üyeler <xref:System.Exception?displayProperty=nameWithType>taban sınıftan devralınır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Exception?displayProperty=nameWithType>
- [MissingMetadataException Sınıfı](missingmetadataexception-class-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
