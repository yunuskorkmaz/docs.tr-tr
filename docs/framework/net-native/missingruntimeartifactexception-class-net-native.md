---
title: MissingRuntimeArtifactException Sınıfı (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
ms.openlocfilehash: 7a69add45202b3ad838de592fadc82a84fa0ba5d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180976"
---
# <a name="missingruntimeartifactexception-class-net-native"></a>MissingRuntimeArtifactException Sınıfı (.NET Yerel)
**Windows 10 için Windows uygulamaları için .NET, yalnızca .NET Native**  
  
 Bir tür veya tür üyesi için meta veriler kullanılabilir olduğunda, ancak uygulanması kaldırıldığında oluşturulan özel durum.  
  
 **Ad alanı:** System. Reflection  
  
> [!IMPORTANT]
> `MissingRuntimeArtifactException`Sınıfı yalnızca .NET Native araç zinciri tarafından dahili kullanıma yöneliktir. Üçüncü taraf kodda kullanılmak üzere değildir veya uygulama kodunuzda özel durumu işlemelisiniz. Bunun yerine, [çalışma zamanı yönergeleri dosyanıza](runtime-directives-rd-xml-configuration-file-reference.md)girdiler ekleyerek özel durumu ortadan kaldırabilirsiniz. Daha fazla bilgi için, açıklamalar bölümüne bakın.  
  
## <a name="syntax"></a>Sözdizimi  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 `MissingRuntimeArtifactException`Sınıfının öğesinden türetildiğine unutmayın <xref:System.MemberAccessException> .  
  
 `MissingRuntimeArtifactException`Sınıfı aşağıdaki üyelere sahiptir:  
  
## <a name="constructors"></a>Oluşturucular  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|`MissingRuntimeArtifactException`Hatayı açıklayan sistem tarafından sağlanan bir ileti kullanarak sınıfının yeni bir örneğini başlatır.<br /><br /> Bu Oluşturucu yalnızca .NET Native araç zinciri tarafından iç kullanım içindir.|  
|`public MissingRuntimeArtifactException(String message)`|Belirtilen bir hata iletisiyle sınıfın yeni bir örneğini başlatır `MissingRuntimeArtifactException` .<br /><br /> Bu Oluşturucu yalnızca .NET Native araç zinciri tarafından iç kullanım içindir.|  
  
## <a name="properties"></a>Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Özel durum hakkında ek kullanıcı tanımlı bilgiler sağlayan anahtar/değer çiftleri koleksiyonunu alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public string HelpLink { get; set; }`|Bu özel durumla ilişkili Yardım dosyasının bağlantısını alır veya ayarlar. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public int HResult { get; protected set; }`|`HRESULT`Belirli bir özel duruma atanan kodlanmış bir sayısal değeri alır veya ayarlar. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public Exception InnerException { get; }`|Geçerli özel duruma neden olan özel durumu alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public string Message { get; }`|Geçerli özel durumu açıklayan bir ileti alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public string Source { get; set; }`|Hataya neden olan uygulamanın veya nesnenin adını alır veya ayarlar. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public string StackTrace { get; }`|Çağrı yığınında anlık çerçevelerin dize gösterimini alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public MethodBase TargetSite { get; }`|Geçerli özel durumu oluşturan yöntemi alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Belirtilen nesnenin geçerli nesneye eşit olup olmadığını belirler.  (Öğesinden devralındı <xref:System.Object> .)|  
|`protected void Finalize()`|Bir nesnenin çöp toplama tarafından geri alınmadan önce kaynakları serbest bırakma ve diğer temizleme işlemlerini gerçekleştirmesine izin verir. (Öğesinden devralındı <xref:System.Object> .)|  
|`public Exception GetBaseException()`|Bir veya daha fazla sonraki özel durumun asıl nedeni olan özel durumu döndürür. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public int GetHashCode()`|Örnek için bir karma kod döndürür `MissingRuntimeArtifactException` .   (Öğesinden devralındı <xref:System.Object> .)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|<xref:System.Runtime.Serialization.SerializationInfo>Özel durumla ilgili bilgileri içeren bir nesne ayarlar.  (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`public Type GetType()`|Geçerli örneğin çalışma zamanı türünü alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
|`protected Object MemberwiseClone()`|Geçerli nesnenin basit bir kopyasını oluşturur. (Öğesinden devralındı <xref:System.Object> .)|  
|`public string ToString()`|Geçerli özel durumun dize gösterimini döndürür. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
  
## <a name="events"></a>Olaylar  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Özel durum hakkında serileştirilmiş veri içeren bir özel durum nesnesi oluşturmak için bir özel durum serileştirildiğinde gerçekleşir. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|  
  
## <a name="usage-details"></a>Kullanım Ayrıntıları  
 `MissingRuntimeArtifactException`Bir tür örneği oluşturmak veya bir tür üyesini çağırmak için bir deneme yapıldığında ve tür ya da üyenin meta verileri mevcut olsa da, uygulamanın kaldırılması, bu özel durum oluşturulur.  
  
 Bir yöntemi dinamik olarak yürütmek için meta verilerin ve uygulama kodunun çalışma zamanında bir uygulama için kullanılabilir olup olmadığı, çalışma zamanı yönergeleri (XML yapılandırma) dosyası, \* . RD. xml tarafından tanımlanır. Uygulamanızın bu özel durumu oluşturmasını engellemek için. RD. xml ' i değiştirmeniz gerekir. Bu, \* bir tür veya tür üyesinin gerek duyduğu meta verilerin çalışma zamanında mevcut olmasını sağlamaktır. . RD. xml dosyasının biçimi hakkında daha fazla bilgi için \* bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
> Bu özel durum, uygulamanız için gereken uygulama kodunun çalışma zamanında kullanılabilir olmadığını gösterdiği için, bu özel durumu bir blokta tutamamalısınız `try` / `catch` . Bunun yerine, özel durumun nedenini tanılamanıza ve bir çalışma zamanı yönergeleri dosyası kullanarak ortadan kaldırmanız gerekir. Genellikle, `Activate` `Dynamic` çalışma zamanı yönergeleri dosyasındaki ( \* . RD. xml dosyası) bir program öğesi için uygun veya ilkeyi belirterek bu özel durumu ortadan kaldırabilirsiniz. Özel durumu ortadan kaldıran çalışma zamanı yönergeleri dosyanıza ekleyebileceğiniz girişi almak için iki sorun gidericinin birini kullanabilirsiniz:  
>
> - Türler için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/type.html) .  
> - Metotlar için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/method.html) .  
  
 `MissingRuntimeArtifactException`Sınıf benzersiz üye içermiyor; tüm üyeleri kendi temel sınıfından devralınır <xref:System.MemberAccessException> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)
