---
title: MissingRuntimeArtifactException Sınıfı (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7b138aec8a64683ca4b42cbbc8bd3584c06cc90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="missingruntimeartifactexception-class-net-native"></a>MissingRuntimeArtifactException Sınıfı (.NET Yerel)
**Windows 10, Windows uygulamaları için .NET [!INCLUDE[net_native](../../../includes/net-native-md.md)] yalnızca**  
  
 Meta veri türü veya tür üyesi için kullanılabilir olmadığında oluşan özel durum ancak uygulaması kaldırıldı.  
  
 **Namespace:** System.Reflection  
  
> [!IMPORTANT]
>  `MissingRuntimeArtifactException` Sınıfı içindir yalnızca tarafından dahili kullanımla [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri. Üçüncü taraf kodu kullanmak için hedeflenmemiş ya da özel durum, uygulama kodunuzda işlemelidir. Bunun yerine, girişlere ekleyerek özel durum ortadan, [çalışma zamanı yönergeleri dosya](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
## <a name="syntax"></a>Sözdizimi  
 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 Unutmayın `MissingRuntimeArtifactException` sınıfı türer <xref:System.MemberAccessException>.  
  
 `MissingRuntimeArtifactException` Sınıfı aşağıdaki üyeleri sahiptir:  
  
## <a name="constructors"></a>Oluşturucular  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|Yeni bir örneğini başlatır `MissingRuntimeArtifactException` hatayı açıklayan sistem tarafından sağlanmış bir iletiyi kullanarak sınıfı.<br /><br /> Bu oluşturucu tarafından dahili kullanımla ilgili olduğu [!INCLUDE[net_native](../../../includes/net-native-md.md)] aracı yalnızca zinciri.|  
|`public MissingRuntimeArtifactException(String message)`|Yeni bir örneğini başlatır `MissingRuntimeArtifactException` belirtilen hata iletisiyle sınıfı.<br /><br /> Bu oluşturucu tarafından dahili kullanımla ilgili olduğu [!INCLUDE[net_native](../../../includes/net-native-md.md)] aracı yalnızca zinciri.|  
  
## <a name="properties"></a>Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Ek kullanıcı tanımlı özel durumla ilgili bilgiler anahtar/değer çiftleri koleksiyonu alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Alır veya bu özel durumla ilgili Yardım dosyası için bir bağlantı ayarlar. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Alır veya ayarlar `HRESULT`, belirli bir özel durum atanan sayısal değer kodlanmış. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Geçerli özel durumun nedeni özel durumu alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Geçerli özel durumu açıklayan bir ileti alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Source { get; set; }`|Alır veya uygulama veya hataya nesnesinin adını ayarlar. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Çağrı yığınındaki hemen çerçeveler dize gösterimini alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Geçerli bir özel durum belirtti yöntemi alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Belirtilen nesnenin geçerli nesneyle eşit olup olmadığını belirler.  (Devralınan <xref:System.Object>.)|  
|`protected void Finalize()`|Kaynakları serbest ve atık toplama tarafından alınmadan önce diğer temizleme işlemleri gerçekleştirmek denemek bir nesne sağlar. (Devralınan <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Bir veya daha fazla sonraki özel kök nedenini özel durum döndürür. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Bir karma kodu döndürür bir `MissingRuntimeArtifactException` örneği.   (Devralınan <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Ayarlar bir <xref:System.Runtime.Serialization.SerializationInfo> özel durum hakkında bilgi içeren nesne.  (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Geçerli örneğin çalışma zamanı türünü alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Geçerli nesne basit bir kopyasını oluşturur. (Devralınan <xref:System.Object>.)|  
|`public string ToString()`|Geçerli özel durumun dize gösterimini döndürür. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Olaylar  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Bir özel durum seri içeren bir özel durum nesnesi oluşturmak için veri özel durumla ilgili serileştirilmiş oluşur. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Kullanım ayrıntıları  
 `MissingRuntimeArtifactException` Bir tür örneği veya türü üyesi çağırmak için bir girişimde ve tür veya üye meta veri mevcut olsa da, kendi uygulama kaldırıldı, özel durum.  
  
 Meta veri ve uygulama kodu dinamik olarak bir yöntem yürütülmeye çalışma zamanında bir uygulama için kullanılabilir olup çalışma zamanı yönergeleri (XML yapılandırması) dosyası tarafından tanımlanan *. rd.xml. Bu özel durum atma uygulamanızı önlemek için değiştirmelisiniz \*. rd.xml türü veya tür üyesi tarafından gerekli meta veri çalışma zamanında mevcut olduğundan emin olun. Biçimi hakkında bilgi için \*. rd.xml dosya bkz [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Bu özel durum, uygulamanız tarafından gerekli uygulama kodu çalışma zamanında kullanılabilir durumda gösterir olduğundan, bu özel durum işleme döndürmemelidir bir `try` / `catch` bloğu. Bunun yerine, özel durumun nedeni tanılamanıza ve bir çalışma zamanı yönergeleri dosyası kullanarak kaldırın. Genellikle, uygun belirterek bu özel durumun ortadan `Activate` veya `Dynamic` çalışma zamanı yönergeleri dosyasındaki bir program öğesi için ilke (*. rd.xml dosyası). Özel durum ortadan kaldırır, çalışma zamanı yönergeleri dosyasına ekleyebilirsiniz giriş almak için iki sorun gidericileri birini kullanabilirsiniz:  
>   
>  -   [MissingMetadataException sorun gidericisini](http://dotnet.github.io/native/troubleshooter/type.html) türleri için.  
> -   [MissingMetadataException sorun gidericisini](http://dotnet.github.io/native/troubleshooter/method.html) yöntemleri için.  
  
 `MissingRuntimeArtifactException` Sınıfı benzersiz üye içeriyor; tüm üyeleri kendi taban sınıfından devralınır <xref:System.MemberAccessException>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Çalışma Zamanı Yönerge İlkesi Ayarları](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
