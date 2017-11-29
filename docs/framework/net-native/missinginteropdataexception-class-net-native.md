---
title: "MissingInteropDataException Sınıfı (.NET Yerel)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: eab4bcf8-9f5f-4731-87d8-842748a6062a
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0a7e1c02b6404f9511032d18f260726d1493d202
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="missinginteropdataexception-class-net-native"></a>MissingInteropDataException Sınıfı (.NET Yerel)
**Windows 10, Windows uygulamaları için .NET [!INCLUDE[net_native](../../../includes/net-native-md.md)] yalnızca**  
  
 Yöntemi hazırlama el ile çağrıldı, ancak meta veri türü için statik çözümleme tarafından veya bir çalışma zamanı yönergeleri dosyasında bulunamadığını zaman oluşturulur özel durum.  
  
 **Namespace:** System.Runtime.CompilerServices  
  
> [!IMPORTANT]
>  `MissingInteropDataException` Sınıfı içindir yalnızca tarafından dahili kullanımla [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri. Üçüncü taraf kodu kullanmak için hedeflenmemiş ya da özel durum, uygulama kodunuzda işlemelidir. Bunun yerine, girişlere ekleyerek özel durum ortadan, [çalışma zamanı yönergeleri dosya](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
## <a name="syntax"></a>Sözdizimi  
 [!code-csharp[ProjectN#21](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missinginteropdataexception_syntax1.cs#21)]
 [!code-vb[ProjectN#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/projectn/vb/missinginteropdataexception_syntax1.vb#21)]  
  
 `MissingInteropDataException` Sınıfı aşağıdaki üyeleri sahiptir:  
  
## <a name="constructors"></a>Oluşturucular  
  
|Oluşturucu|Açıklama|  
|-----------------|-----------------|  
|`public MissingInteropDataException(String resourceId, Type pertinentType)`|Yeni bir örneğini başlatır `MissingInteropDataException` hata ve verileri eksik türü açıklayan sistem tarafından sağlanmış bir ileti kimliği kullanarak sınıfı. Bu oluşturucu tarafından dahili kullanımla ilgili olduğu [!INCLUDE[net_native](../../../includes/net-native-md.md)] aracı yalnızca zinciri.|  
  
## <a name="properties"></a>Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|Ek kullanıcı tanımlı özel durumla ilgili bilgiler anahtar/değer çiftleri koleksiyonu alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string HelpLink { get; set; }`|Alır veya bu özel durumla ilgili Yardım dosyası için bir bağlantı ayarlar. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int HResult { get; protected set; }`|Alır veya ayarlar `HRESULT`, belirli bir özel durum atanan kodlanmış bir sayısal değer olduğu. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Exception InnerException { get; }`|Geçerli özel durumun nedeni özel durumu alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string Message { get; }`|Geçerli özel durumu açıklayan bir ileti alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type MissingType { get; private set; }`|Türünü alır veya verileri eksik ayarlar.|  
|`public string Source { get; set; }`|Alır veya uygulama veya hataya nesnesinin adını ayarlar. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public string StackTrace { get; }`|Çağrı yığınındaki hemen çerçeveler dize gösterimini alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public MethodBase TargetSite { get; }`|Geçerli bir özel durum belirtti yöntemi alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|Belirtilen nesnenin geçerli nesneyle eşit olup olmadığını belirler.  (Devralınan <xref:System.Object>.)|  
|`protected void Finalize()`|Kaynakları serbest ve atık toplama tarafından alınmadan önce diğer temizleme işlemleri gerçekleştirmek denemek bir nesne sağlar. (Devralınan <xref:System.Object>.)|  
|`public Exception GetBaseException()`|Bir veya daha fazla sonraki özel kök nedenini özel durum döndürür. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public int GetHashCode()`|Bir karma kodu döndürür bir `MissingInteropDataException` örneği.   (Devralınan <xref:System.Object>.)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Ayarlar bir <xref:System.Runtime.Serialization.SerializationInfo> özel durum hakkında bilgi içeren nesne.  (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`public Type GetType()`|Geçerli örneğin çalışma zamanı türünü alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
|`protected Object MemberwiseClone()`|Geçerli nesne basit bir kopyasını oluşturur. (Devralınan <xref:System.Object>.)|  
|`public string ToString()`|Geçerli özel durumun dize gösterimini döndürür. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="events"></a>Olaylar  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Bir özel durum seri içeren bir özel durum nesnesi oluşturmak için veri özel durumla ilgili serileştirilmiş oluşur. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|  
  
## <a name="usage-details"></a>Kullanım ayrıntıları  
 `MissingInteropDataException` Türü bilgileri kullanılamadığı için bir COM veya Windows çalışma zamanı bileşeni için bir yöntem çağrısı başarıyla yapılamaz, özel durum.  
  
 Çalışma zamanında bir uygulama için kullanılabilir meta veri çalışma zamanı yönergeleri (XML yapılandırması) dosyası tarafından tanımlanan *. rd.xml. Bu özel durum atma uygulamanızı önlemek için çalışma zamanında bulunmalıdır meta verileri tanımlamak için bu dosyayı değiştirmeniz gerekir. En yaygın olarak ekleyerek bu hatayı gidermek bir `MarshalObject`, `MarshalDelegate`, veya `MarshalStructure` uygun bir program öğesi çalışma zamanı yönergeleri dosyasında özniteliği. Bu dosya biçimi hakkında daha fazla bilgi için bkz: [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Bu durum, uygulamanız tarafından gerekli meta verilerin çalışma zamanında kullanılamaz gösterir olduğundan, bu özel durum işleme döndürmemelidir bir `try` / `catch` bloğu. Bunun yerine, özel durumun nedeni tanılamanıza ve uygun girdiyi bir çalışma zamanı yönergeleri dosyasına ekleyerek ortadan kaldırmak.  
  
 `MissingInteropDataException` Sınıfı içeren tek bir benzersiz üye `MissingType` olan meta veri başarılı yöntem çağrısı için gereken türünü gösteren özelliği. Tüm kalan üyeleri taban sınıfından devralınır <xref:System.Exception?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Exception?displayProperty=nameWithType>  
 [MissingMetadataException sınıfı](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)  
 [Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
