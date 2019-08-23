---
title: MissingRuntimeArtifactException Sınıfı (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: caa929225701a62c0abb3b335bfd7fb6a129e9e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941634"
---
# <a name="missingruntimeartifactexception-class-net-native"></a>MissingRuntimeArtifactException Sınıfı (.NET Yerel)
**Windows 10 için Windows uygulamaları için .NET, yalnızca .NET Native**  
  
 Bir tür veya tür üyesi için meta veriler kullanılabilir olduğunda, ancak uygulanması kaldırıldığında oluşturulan özel durum.  
  
 **Uzayına** System. Reflection  
  
> [!IMPORTANT]
> `MissingRuntimeArtifactException` Sınıfı yalnızca .NET Native araç zinciri tarafından dahili kullanıma yöneliktir. Üçüncü taraf kodda kullanılmak üzere değildir veya uygulama kodunuzda özel durumu işlemelisiniz. Bunun yerine, [çalışma zamanı yönergeleri dosyanıza](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)girdiler ekleyerek özel durumu ortadan kaldırabilirsiniz. Daha fazla bilgi için, açıklamalar bölümüne bakın.  
  
## <a name="syntax"></a>Sözdizimi  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 `MissingRuntimeArtifactException` Sınıfının öğesinden<xref:System.MemberAccessException>türetildiğine unutmayın.  
  
 `MissingRuntimeArtifactException` Sınıfı aşağıdaki üyelere sahiptir:  
  
## <a name="constructors"></a>Oluşturucular  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|Hatayı açıklayan sistem tarafından sağlanan bir `MissingRuntimeArtifactException` ileti kullanarak sınıfının yeni bir örneğini başlatır.<br /><br /> Bu Oluşturucu yalnızca .NET Native araç zinciri tarafından iç kullanım içindir.|  
|`public MissingRuntimeArtifactException(String message)`|Yeni bir örneğini başlatır `MissingRuntimeArtifactException` belirtilen hata iletisiyle sınıfı.<br /><br /> Bu Oluşturucu yalnızca .NET Native araç zinciri tarafından iç kullanım içindir.|  
  
## <a name="properties"></a>Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Özel durum hakkında ek kullanıcı tanımlı bilgiler sağlayan anahtar/değer çiftleri koleksiyonunu alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public string HelpLink { get; set; }`|Bu özel durumla ilişkili Yardım dosyasının bağlantısını alır veya ayarlar. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public int HResult { get; protected set; }`|Belirli bir özel duruma `HRESULT`atanan kodlanmış bir sayısal değeri alır veya ayarlar. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public Exception InnerException { get; }`|Geçerli özel duruma neden olan özel durumu alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public string Message { get; }`|Geçerli özel durumu açıklayan bir ileti alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public string Source { get; set; }`|Hataya neden olan uygulamanın veya nesnenin adını alır veya ayarlar. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public string StackTrace { get; }`|Çağrı yığınında anlık çerçevelerin dize gösterimini alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public MethodBase TargetSite { get; }`|Geçerli özel durumu oluşturan yöntemi alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Belirtilen nesnenin geçerli nesneyle eşit olup olmadığını belirler.  (Öğesinden <xref:System.Object>devralındı.)|  
|`protected void Finalize()`|Bir nesnenin çöp toplama tarafından geri alınmadan önce kaynakları serbest bırakma ve diğer temizleme işlemlerini gerçekleştirmesine izin verir. (Öğesinden <xref:System.Object>devralındı.)|  
|`public Exception GetBaseException()`|Bir veya daha fazla sonraki özel durumun asıl nedeni olan özel durumu döndürür. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public int GetHashCode()`|`MissingRuntimeArtifactException` Örnek için bir karma kod döndürür.   (Öğesinden <xref:System.Object>devralındı.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Özel durumla <xref:System.Runtime.Serialization.SerializationInfo> ilgili bilgileri içeren bir nesne ayarlar.  (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public Type GetType()`|Geçerli örneğin çalışma zamanı türünü alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`protected Object MemberwiseClone()`|Geçerli nesnenin basit bir kopyasını oluşturur. (Öğesinden <xref:System.Object>devralındı.)|  
|`public string ToString()`|Geçerli özel durumun dize gösterimini döndürür. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
  
## <a name="events"></a>Olaylar  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Özel durum hakkında serileştirilmiş veri içeren bir özel durum nesnesi oluşturmak için bir özel durum serileştirildiğinde gerçekleşir. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
  
## <a name="usage-details"></a>Kullanım ayrıntıları  
 Bir tür örneği oluşturmak veya bir tür üyesini çağırmak için bir deneme yapıldığında ve tür ya da üyenin meta verileri mevcut olsa da, uygulamanın kaldırılması, bu özeldurumoluşturulur.`MissingRuntimeArtifactException`  
  
 Bir yöntemi dinamik olarak yürütmek için meta verilerin ve uygulama kodunun çalışma zamanında bir uygulama için kullanılabilir olup olmadığı, çalışma zamanı yönergeleri (XML yapılandırma) dosyası, \*. RD. xml tarafından tanımlanır. Uygulamanızın bu özel durumu oluşturmasını engellemek için. RD. xml ' \*i değiştirmeniz gerekir. Bu, bir tür veya tür üyesinin gerek duyduğu meta verilerin çalışma zamanında mevcut olmasını sağlamaktır. \*. RD. xml dosyasının biçimi hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
> Bu özel durum, uygulamanız için gereken uygulama kodunun çalışma zamanında kullanılabilir olmadığını gösterdiği için, bu özel durumu bir `try` / `catch` blokta tutamamalısınız. Bunun yerine, özel durumun nedenini tanılamanıza ve bir çalışma zamanı yönergeleri dosyası kullanarak ortadan kaldırmanız gerekir. Genellikle, çalışma zamanı yönergeleri dosyasındaki ( `Activate` \*. RD. xml `Dynamic` dosyası) bir program öğesi için uygun veya ilkeyi belirterek bu özel durumu ortadan kaldırabilirsiniz. Özel durumu ortadan kaldıran çalışma zamanı yönergeleri dosyanıza ekleyebileceğiniz girişi almak için iki sorun gidericinin birini kullanabilirsiniz:  
>   
> - Türler için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/type.html) .  
> - Metotlar için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/method.html) .  
  
 Sınıf benzersiz üye içermiyor; tüm üyeleri kendi temel <xref:System.MemberAccessException>sınıfından devralınır. `MissingRuntimeArtifactException`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
