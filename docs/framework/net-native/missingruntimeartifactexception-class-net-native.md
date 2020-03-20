---
title: MissingRuntimeArtifactException Sınıfı (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
ms.openlocfilehash: 7a69add45202b3ad838de592fadc82a84fa0ba5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180976"
---
# <a name="missingruntimeartifactexception-class-net-native"></a>MissingRuntimeArtifactException Sınıfı (.NET Yerel)
**.WINDOWS uygulamaları için .NET, sadece .NET Native**  
  
 Bir tür veya tür üyesi için meta veri kullanılabilir olduğunda atılan ancak uygulaması kaldırılan özel durum.  
  
 **Ad alanı:** System.Reflection  
  
> [!IMPORTANT]
> Sınıf `MissingRuntimeArtifactException` yalnızca .NET Native araç zinciri tarafından dahili kullanım için tasarlanmıştır. Üçüncü taraf kodunda kullanılmak üzere tasarlanmamıştır ve uygulama kodunuzdaki özel durumu işlememelisiniz. Bunun yerine, çalışma zamanı yönergeleri dosyanıza girişler ekleyerek özel durumu ortadan [kaldırırsınız.](runtime-directives-rd-xml-configuration-file-reference.md) Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
## <a name="syntax"></a>Sözdizimi  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 `MissingRuntimeArtifactException` Sınıfın ' dan <xref:System.MemberAccessException>türediğini unutmayın.  
  
 Sınıfın `MissingRuntimeArtifactException` aşağıdaki üyeleri vardır:  
  
## <a name="constructors"></a>Oluşturucular  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|Hatayı açıklayan bir sistem `MissingRuntimeArtifactException` tarafından sağlanan ileti kullanarak sınıfın yeni bir örneğini başolarak karşılar.<br /><br /> Bu oluşturucu yalnızca .NET Native araç zinciri tarafından dahili kullanım içindir.|  
|`public MissingRuntimeArtifactException(String message)`|Sınıfın yeni bir örneğini `MissingRuntimeArtifactException` belirli bir hata iletisiyle başolarak adlandırır.<br /><br /> Bu oluşturucu yalnızca .NET Native araç zinciri tarafından dahili kullanım içindir.|  
  
## <a name="properties"></a>Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Özel durum hakkında kullanıcı tarafından tanımlanan ek bilgiler sağlayan anahtar/değer çiftleri koleksiyonu alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Bu özel durumla ilişkili yardım dosyasına bir bağlantı alır veya ayarlar. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Belirli bir `HRESULT`özel durum için atanan, kodlanmış sayısal değeri alır veya ayarlar. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Geçerli özel durum neden özel durum alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Geçerli özel durumu açıklayan bir ileti alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Source { get; set; }`|Hataya neden olan uygulamanın veya nesnenin adını alır veya ayarlar. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Çağrı yığınındaki hemen karelerin dize temsilini alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Geçerli özel durum attı yöntemi alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Belirtilen nesnenin geçerli nesneye eşit olup olmadığını belirler.  (Devralınan <xref:System.Object>.)|  
|`protected void Finalize()`|Bir nesnenin, çöp toplama tarafından geri verilmeden önce kaynakları serbest kılmaya ve diğer temizleme işlemlerini gerçekleştirmeye çalışmasına izin verir. (Devralınan <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Bir veya daha fazla sonraki özel durumların temel nedeni olan özel durumu döndürür. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Bir `MissingRuntimeArtifactException` örnek için karma kod döndürür.   (Devralınan <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Özel <xref:System.Runtime.Serialization.SerializationInfo> durum hakkında bilgi içeren bir nesne ayarlar.  (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Geçerli örneğin çalışma zamanı türünü alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Geçerli nesnenin sığ bir kopyasını oluşturur. (Devralınan <xref:System.Object>.)|  
|`public string ToString()`|Geçerli özel durum dize temsilini verir. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Olaylar  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Özel durum hakkında serileştirilmiş veri içeren bir özel durum durumu nesnesi oluşturmak için serileştirilmiş bir özel durum oluşur. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Kullanım Ayrıntıları  
 Özel `MissingRuntimeArtifactException` durum, bir türe anında bir kez çağrılması veya bir tür üyesinin çağrılması girişimi yapıldığında ve tür veya üyenin meta verileri bulunmasına rağmen, uygulanması kaldırıldığında atılır.  
  
 Meta verilerin ve bir yöntemi dinamik olarak yürütmek için uygulama kodunun bir uygulamanın çalışma zamanında kullanıp kullanılamayacağı çalışma zamanı yönergeleri (XML yapılandırması) dosyası , \*.rd.xml tarafından tanımlanır. Uygulamanızın bu özel durumu atmasını \*önlemek için, bir tür veya tür üyesinin ihtiyaç duyduğu meta verilerin çalışma zamanında mevcut olduğundan emin olmak için .rd.xml'i değiştirmeniz gerekir. \*.rd.xml dosyasının biçimi hakkında bilgi için [Runtime Yönergeleri (rd.xml) Yapılandırma Dosya Başvurusu'na](runtime-directives-rd-xml-configuration-file-reference.md)bakın.  
  
> [!IMPORTANT]
> Bu özel durum, uygulamanız tarafından gereken uygulama kodunun çalışma zamanında kullanılmadığını gösterdiğinden, bu özel durumu bir `try` / `catch` blokta işlememeniz gerekir. Bunun yerine, özel durum nedenini tanılamak ve bir çalışma zamanı yönergeleri dosyası kullanarak ortadan kaldırmak gerekir. Genellikle, çalışma zamanı yönergeleri dosyasında `Activate` (.rd.xml `Dynamic` \*dosyası) bir program öğesi için uygun veya ilke belirterek bu özel durumu ortadan kaldırırsınız. Özel durumu ortadan kaldıran çalışma zamanı yönergeleri dosyanıza ekleyebileceğiniz girişi almak için iki sorun gidericiden birini kullanabilirsiniz:  
>
> - Türleri için [MissingMetadataException sorun giderici.](https://dotnet.github.io/native/troubleshooter/type.html)  
> - Yöntemler için [Eksik MetadataException sorun giderici.](https://dotnet.github.io/native/troubleshooter/method.html)  
  
 Sınıf `MissingRuntimeArtifactException` benzersiz üye içermez; tüm üyeleri, kendi taban sınıfından <xref:System.MemberAccessException>devralınır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)
