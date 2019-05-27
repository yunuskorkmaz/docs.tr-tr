---
title: MissingInteropDataException Sınıfı (.NET Yerel)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eab4bcf8-9f5f-4731-87d8-842748a6062a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 803709c97309f9766b6a441f5521cdcd7504862f
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052497"
---
# <a name="missinginteropdataexception-class-net-native"></a>MissingInteropDataException Sınıfı (.NET Yerel)
**Windows 10, yalnızca .NET yerel Windows uygulamaları için .NET**  
  
 Yöntem hazırlama el ile olarak adlandırılır, ancak bir türü için meta verileri statik analiz tarafından veya bir çalışma zamanı yönergeleri dosyası bulunamadıysa oluşturulan özel durum.  
  
 **Namespace:** System.Runtime.CompilerServices  
  
> [!IMPORTANT]
>  `MissingInteropDataException` Sınıfı, .NET Native araç zinciri tarafından yalnızca iç kullanım için tasarlanmıştır. Üçüncü taraf kodu kullanmak için hedeflenmemiş ya da uygulama kodunuzda bir özel durum işlemesi gerekir. Bunun yerine, girişlere ekleyerek özel durumu ortadan, [çalışma zamanı yönergeleri dosyası](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
## <a name="syntax"></a>Sözdizimi  
 [!code-csharp[ProjectN#21](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missinginteropdataexception_syntax1.cs#21)]
 [!code-vb[ProjectN#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/projectn/vb/missinginteropdataexception_syntax1.vb#21)]  
  
 `MissingInteropDataException` Sınıfı aşağıdaki üyelere sahiptir:  
  
## <a name="constructors"></a>Oluşturucular  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`public MissingInteropDataException(String resourceId, Type pertinentType)`|Yeni bir örneğini başlatır `MissingInteropDataException` hataya ve verileri eksik tür açıklayan sistem tarafından sağlanmış bir iletinin Kimliğini kullanarak sınıfı. Bu oluşturucu yalnızca .NET yerel araç zinciri tarafından iç kullanım içindir.|  
  
## <a name="properties"></a>Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Özel durum hakkında ek kullanıcı tanımlı bilgi sağlayan anahtar/değer çiftlerinin koleksiyonunu alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Alır veya bir bağlantıyı bu durumla ilişkili Yardım dosyasını ayarlar. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Alır veya ayarlar `HRESULT`, belirli bir özel durum için atanan kodlanmış bir sayısal değer olduğu. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Geçerli özel duruma neden özel durumu alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Geçerli özel durumu açıklayan bir ileti alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type MissingType { get; private set; }`|Türünü alır veya verisini eksik ayarlar.|  
|`public string Source { get; set; }`|Alır veya ayarlar uygulama ya da hataya neden nesnesinin adı. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Çağrı yığınındaki hemen çerçeveleri dize gösterimini alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Geçerli özel durum oluşturdu yöntemi alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Belirtilen nesnenin geçerli nesneyle eşit olup olmadığını belirler.  (Devralınan <xref:System.Object>.)|  
|`protected void Finalize()`|Ücretsiz kaynaklar ve çöp toplamanın alınmadan önce diğer temizleme işlemleri gerçekleştirmesini denemek bir nesne sağlar. (Devralınan <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Bir veya daha fazla sonraki özel durumların kök nedenini özel durum verir. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Bir karma kodu döndürür bir `MissingInteropDataException` örneği.   (Devralınan <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Ayarlar bir <xref:System.Runtime.Serialization.SerializationInfo> özel durum hakkında bilgi içeren nesne.  (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Geçerli örneğin çalışma zamanı türünü alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Geçerli nesne basit bir kopyasını oluşturur. (Devralınan <xref:System.Object>.)|  
|`public string ToString()`|Geçerli özel durumun dize gösterimini döndürür. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Olaylar  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Özel durum hakkında veri içeren bir özel durum nesnesi oluşturmak için seri hale getirilmiş bir özel durum serileştirilmiş olduğunda gerçekleşir. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Kullanım ayrıntıları  
 `MissingInteropDataException` Tür bilgileri kullanılamadığı için bir yöntem çağrısını bir COM veya Windows çalışma zamanı bileşeni başarıyla yapılamaz, özel durum harekete geçirilir.  
  
 Çalışma zamanında bir uygulama için kullanılabilir meta veri çalışma zamanı yönergeleri (XML yapılandırması) dosyası tarafından tanımlanan *. rd.xml. Bu özel durum gelen uygulamanızı önlemek için çalışma zamanında bulunması gereken meta verileri tanımlamak için bu dosyayı değiştirmeniz gerekir. En yaygın olarak ekleyerek bu hatayı gidermek bir `MarshalObject`, `MarshalDelegate`, veya `MarshalStructure` uygun programı öğenin çalışma zamanı yönergeleri dosya özniteliği. Bu dosya biçimi hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Bu özel durumun, uygulamanızın ihtiyaç duyduğu meta verilerin çalışma zamanında kullanılamaz belirttiğinden, bu özel durum işleme karakteri bir `try` / `catch` blok. Bunun yerine, özel durumun nedenini tanılayın ve uygun girdiyi bir çalışma zamanı yönergeleri dosyasına ekleyerek ortadan kaldırın.  
  
 `MissingInteropDataException` Sınıfı içeren tek bir benzersiz üye `MissingType` olan meta verileri için başarılı bir yöntem çağrısı gerekli türünü gösteren özellik. Temel sınıftan devralınan tüm kalan üyeleri <xref:System.Exception?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Exception?displayProperty=nameWithType>
- [MissingMetadataException Sınıfı](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
