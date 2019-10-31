---
title: MissingRuntimeArtifactException Sınıfı (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
ms.openlocfilehash: 58c18fa2d83422e757511d9d2a93606b0a360086
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128299"
---
# <a name="missingruntimeartifactexception-class-net-native"></a>MissingRuntimeArtifactException Sınıfı (.NET Yerel)
**Windows 10 için Windows uygulamaları için .NET, yalnızca .NET Native**  
  
 Bir tür veya tür üyesi için meta veriler kullanılabilir olduğunda, ancak uygulanması kaldırıldığında oluşturulan özel durum.  
  
 **Ad alanı:** System. Reflection  
  
> [!IMPORTANT]
> `MissingRuntimeArtifactException` sınıfı, yalnızca .NET Native araç zinciri tarafından dahili kullanıma yöneliktir. Üçüncü taraf kodda kullanılmak üzere değildir veya uygulama kodunuzda özel durumu işlemelisiniz. Bunun yerine, [çalışma zamanı yönergeleri dosyanıza](runtime-directives-rd-xml-configuration-file-reference.md)girdiler ekleyerek özel durumu ortadan kaldırabilirsiniz. Daha fazla bilgi için, açıklamalar bölümüne bakın.  
  
## <a name="syntax"></a>Sözdizimi  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 `MissingRuntimeArtifactException` sınıfının <xref:System.MemberAccessException>türediğini unutmayın.  
  
 `MissingRuntimeArtifactException` sınıfı aşağıdaki üyelere sahiptir:  
  
## <a name="constructors"></a>Oluşturucular  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|Hatayı açıklayan sistem tarafından sağlanan bir ileti kullanarak `MissingRuntimeArtifactException` sınıfının yeni bir örneğini başlatır.<br /><br /> Bu Oluşturucu yalnızca .NET Native araç zinciri tarafından iç kullanım içindir.|  
|`public MissingRuntimeArtifactException(String message)`|Belirtilen bir hata iletisiyle `MissingRuntimeArtifactException` sınıfının yeni bir örneğini başlatır.<br /><br /> Bu Oluşturucu yalnızca .NET Native araç zinciri tarafından iç kullanım içindir.|  
  
## <a name="properties"></a>Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Özel durum hakkında ek kullanıcı tanımlı bilgiler sağlayan anahtar/değer çiftleri koleksiyonunu alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public string HelpLink { get; set; }`|Bu özel durumla ilişkili Yardım dosyasının bağlantısını alır veya ayarlar. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public int HResult { get; protected set; }`|Belirli bir özel duruma atanan kodlanmış sayısal değeri `HRESULT`alır veya ayarlar. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public Exception InnerException { get; }`|Geçerli özel duruma neden olan özel durumu alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public string Message { get; }`|Geçerli özel durumu açıklayan bir ileti alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public string Source { get; set; }`|Hataya neden olan uygulamanın veya nesnenin adını alır veya ayarlar. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public string StackTrace { get; }`|Çağrı yığınında anlık çerçevelerin dize gösterimini alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public MethodBase TargetSite { get; }`|Geçerli özel durumu oluşturan yöntemi alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Belirtilen nesnenin geçerli nesneyle eşit olup olmadığını belirler.  (<xref:System.Object>devralındı.)|  
|`protected void Finalize()`|Bir nesnenin çöp toplama tarafından geri alınmadan önce kaynakları serbest bırakma ve diğer temizleme işlemlerini gerçekleştirmesine izin verir. (<xref:System.Object>devralındı.)|  
|`public Exception GetBaseException()`|Bir veya daha fazla sonraki özel durumun asıl nedeni olan özel durumu döndürür. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public int GetHashCode()`|`MissingRuntimeArtifactException` örneği için bir karma kod döndürür.   (<xref:System.Object>devralındı.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Özel durum hakkında bilgi içeren bir <xref:System.Runtime.Serialization.SerializationInfo> nesnesi ayarlar.  (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`public Type GetType()`|Geçerli örneğin çalışma zamanı türünü alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
|`protected Object MemberwiseClone()`|Geçerli nesnenin basit bir kopyasını oluşturur. (<xref:System.Object>devralındı.)|  
|`public string ToString()`|Geçerli özel durumun dize gösterimini döndürür. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
  
## <a name="events"></a>Olaylar  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Özel durum hakkında serileştirilmiş veri içeren bir özel durum nesnesi oluşturmak için bir özel durum serileştirildiğinde gerçekleşir. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|  
  
## <a name="usage-details"></a>Kullanım ayrıntıları  
 `MissingRuntimeArtifactException` özel durumu, bir tür örneği oluşturmak veya bir tür üyesini çağırmak için bir deneme yapıldığında ve tür ya da üyenin meta verileri mevcut olsa da, uygulamanın kaldırılmış olması durumunda oluşturulur.  
  
 Bir yöntemi dinamik olarak yürütmeye yönelik meta verilerin ve uygulama kodunun çalışma zamanında bir uygulama için kullanılabilir olup olmadığı, çalışma zamanı yönergeleri (XML yapılandırma) dosyası \*. RD. xml tarafından tanımlanır. Uygulamanızın bu özel durumu oluşturmasını engellemek için \*. RD. xml ' yi değiştirerek bir tür veya tür üyesinin ihtiyaç duyduğu meta verilerin çalışma zamanında mevcut olduğundan emin olun. \*. RD. xml dosyasının biçimi hakkında daha fazla bilgi için bkz. [Runtime yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
> Bu özel durum, uygulamanız için gereken uygulama kodunun çalışma zamanında kullanılabilir olmadığını gösterdiği için, bu özel durumu bir `try`/`catch` bloğunda işlememeniz gerekir. Bunun yerine, özel durumun nedenini tanılamanıza ve bir çalışma zamanı yönergeleri dosyası kullanarak ortadan kaldırmanız gerekir. Genellikle, çalışma zamanı yönergeleri dosyasındaki (\*. RD. xml dosyası) bir program öğesi için uygun `Activate` veya `Dynamic` ilkesini belirterek bu özel durumu ortadan kaldırabilirsiniz. Özel durumu ortadan kaldıran çalışma zamanı yönergeleri dosyanıza ekleyebileceğiniz girişi almak için iki sorun gidericinin birini kullanabilirsiniz:  
>   
> - Türler için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/type.html) .  
> - Metotlar için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/method.html) .  
  
 `MissingRuntimeArtifactException` sınıfı benzersiz üye içermiyor; tüm üyeleri, <xref:System.MemberAccessException>temel sınıfından devralınır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)
