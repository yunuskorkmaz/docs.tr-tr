---
title: MissingRuntimeArtifactException Sınıfı (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1fa27a713890f2988a2fcd7983630080dc21d05
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50202165"
---
# <a name="missingruntimeartifactexception-class-net-native"></a>MissingRuntimeArtifactException Sınıfı (.NET Yerel)
**Windows 10 için Windows uygulamaları için .NET [!INCLUDE[net_native](../../../includes/net-native-md.md)] yalnızca**  
  
 Bir tür veya üye türü için meta veriler kullanılabilir olduğunda oluşturulan özel durum ancak uygulanması kaldırıldı.  
  
 **Namespace:** System.Reflection  
  
> [!IMPORTANT]
>  `MissingRuntimeArtifactException` Sınıfı tarafından iç kullanım için yalnızca amaçlanmıştır [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri. Üçüncü taraf kodu kullanmak için hedeflenmemiş ya da uygulama kodunuzda bir özel durum işlemesi gerekir. Bunun yerine, girişlere ekleyerek özel durumu ortadan, [çalışma zamanı yönergeleri dosyası](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
## <a name="syntax"></a>Sözdizimi  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 Unutmayın `MissingRuntimeArtifactException` sınıf türetilir <xref:System.MemberAccessException>.  
  
 `MissingRuntimeArtifactException` Sınıfı aşağıdaki üyelere sahiptir:  
  
## <a name="constructors"></a>Oluşturucular  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|Yeni bir örneğini başlatır `MissingRuntimeArtifactException` hatayı açıklayan sistem tarafından sağlanmış bir iletiyi kullanarak sınıfı.<br /><br /> Bu oluşturucu iç kullanım içindir [!INCLUDE[net_native](../../../includes/net-native-md.md)] aracı yalnızca zinciri.|  
|`public MissingRuntimeArtifactException(String message)`|Yeni bir örneğini başlatır `MissingRuntimeArtifactException` belirtilen hata iletisiyle sınıfı.<br /><br /> Bu oluşturucu iç kullanım içindir [!INCLUDE[net_native](../../../includes/net-native-md.md)] aracı yalnızca zinciri.|  
  
## <a name="properties"></a>Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Özel durum hakkında ek kullanıcı tanımlı bilgi sağlayan anahtar/değer çiftlerinin koleksiyonunu alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Alır veya bir bağlantıyı bu durumla ilişkili Yardım dosyasını ayarlar. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Alır veya ayarlar `HRESULT`, belirli bir özel durum için atanan sayısal değer kodlanmış. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Geçerli özel duruma neden özel durumu alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Geçerli özel durumu açıklayan bir ileti alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Source { get; set; }`|Alır ya da uygulama veya hataya neden olan nesnenin adını ayarlar. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Çağrı yığınındaki hemen çerçeveleri dize gösterimini alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Geçerli özel durum oluşturdu yöntemi alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Belirtilen nesnenin geçerli nesneyle eşit olup olmadığını belirler.  (Devralınan <xref:System.Object>.)|  
|`protected void Finalize()`|Ücretsiz kaynaklar ve çöp toplamanın alınmadan önce diğer temizleme işlemleri gerçekleştirmesini denemek bir nesne sağlar. (Devralınan <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Bir veya daha fazla sonraki özel durumların kök nedenini özel durum verir. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Bir karma kodu döndürür bir `MissingRuntimeArtifactException` örneği.   (Devralınan <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Ayarlar bir <xref:System.Runtime.Serialization.SerializationInfo> özel durum hakkında bilgi içeren nesne.  (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Geçerli örneğin çalışma zamanı türünü alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Geçerli nesne basit bir kopyasını oluşturur. (Devralınan <xref:System.Object>.)|  
|`public string ToString()`|Geçerli özel durumun dize gösterimini döndürür. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Olaylar  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Özel durum hakkında veri içeren bir özel durum nesnesi oluşturmak için seri hale getirilmiş bir özel durum serileştirilmiş olduğunda gerçekleşir. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Kullanım ayrıntıları  
 `MissingRuntimeArtifactException` Bir tür örneği veya bir tür üyesi çağırmak için bir girişimde tür veya üyenin meta verileri mevcut olsa da, kendi uygulama kaldırıldı, özel durum harekete geçirilir.  
  
 Meta veri ve uygulama kodunu dinamik olarak bir yöntem yürütülmeye çalışıldı çalışma zamanında bir uygulama için kullanılabilir olup olmadığı çalışma zamanı yönergeleri (XML yapılandırması) dosyası tarafından tanımlanan \*. rd.xml. Bu özel durum gelen uygulamanızı önlemek için değiştirmelisiniz \*. rd.xml türü veya tür üyesi tarafından gerekli meta verileri çalışma zamanında mevcut olduğundan emin olun. Biçimi hakkında bilgi için \*. rd.xml dosya bkz [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Bu özel durumun, uygulamanızın ihtiyaç duyduğu uygulama kodu çalışma zamanında kullanılabilir olmadığını gösterir çünkü bu özel durum işleme karakteri bir `try` / `catch` blok. Bunun yerine, özel durumun nedenini tanılamak ve çalışma zamanı yönergeleri dosyasını kullanarak kaldırın. Genellikle, uygun belirterek bu özel durumun ortadan `Activate` veya `Dynamic` çalışma zamanı yönergeleri dosyası içindeki bir program öğesi için ilke (\*. rd.xml dosyası). Özel durum ortadan kaldırır, çalışma zamanı yönergeleri dosyasına ekleyebilirsiniz girişini almak için iki sorun gidericileri birini kullanabilirsiniz:  
>   
> - [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/type.html) türleri için.  
> - [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/method.html) yöntemleri için.  
  
 `MissingRuntimeArtifactException` Sınıfı benzersiz üye içeriyor; tüm üyelerini kendi temel sınıfından devralınır <xref:System.MemberAccessException>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Çalışma Zamanı Yönerge İlkesi Ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
