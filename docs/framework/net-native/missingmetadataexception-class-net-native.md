---
title: MissingMetadataException Sınıfı (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: 408f25c4-6d60-475c-92b1-7b52b777c6db
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2961a4c02d8ffe17055307094f56a03680d1a59a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357137"
---
# <a name="missingmetadataexception-class-net-native"></a>MissingMetadataException Sınıfı (.NET Yerel)

**Windows 10 için Windows uygulamaları için .NET [!INCLUDE[net_native](../../../includes/net-native-md.md)] yalnızca**

Yansıma mevcut olmayan meta verilerini almak için kullanıldığında oluşan özel durum.

**Namespace:** System.Reflection

> [!IMPORTANT]
> `MissingMetadataException` Sınıfı tarafından iç kullanım için yalnızca amaçlanmıştır [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri. Üçüncü taraf kodu kullanmak için hedeflenmemiş ya da uygulama kodunuzda bir özel durum işlemesi gerekir. Bunun yerine, girişlere ekleyerek özel durumu ortadan, [çalışma zamanı yönergeleri dosyası](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Daha fazla bilgi için Açıklamalar bölümüne bakın.

## <a name="syntax"></a>Sözdizimi

[!code-csharp[ProjectN#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingmetadataexception_syntax1.cs#4)]

Unutmayın `MissingMetadataException` sınıf türetilir <xref:System.TypeAccessException>.

`MissingMetadataException` Sınıfı aşağıdaki üyelere sahiptir:

## <a name="constructors"></a>Oluşturucular

|Oluşturucu|Açıklama|
|-----------------|-----------------|
|`public MissingMetadataException()`|Yeni bir örneğini başlatır `MissingMetadataException` hatayı açıklayan sistem tarafından sağlanmış bir iletiyi kullanarak sınıfı.<br /><br /> Bu oluşturucu iç kullanım içindir [!INCLUDE[net_native](../../../includes/net-native-md.md)] aracı yalnızca zinciri.|
|`public MissingMetadataException(String message)`|Yeni bir örneğini başlatır `MissingMetadataException` belirtilen hata iletisiyle sınıfı.<br /><br /> Bu oluşturucu iç kullanım içindir [!INCLUDE[net_native](../../../includes/net-native-md.md)] aracı yalnızca zinciri.|

## <a name="properties"></a>Özellikler

|Özellik|Açıklama|
|--------------|-----------------|
|`public IDictionary Data { get; }`|Özel durum hakkında ek kullanıcı tanımlı bilgi sağlayan anahtar/değer çiftlerinin koleksiyonunu alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string HelpLink { get; set; }`|Alır veya bir bağlantıyı bu durumla ilişkili Yardım dosyasını ayarlar. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|
|`public int HResult { get; protected set; }`|Alır veya ayarlar `HRESULT`, belirli bir özel durum için atanan sayısal değer kodlanmış. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|
|`public Exception InnerException { get; }`|Geçerli özel duruma neden özel durumu alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string Message { get; }`|Geçerli özel durumu açıklayan bir ileti alır. (Devralınan <xref:System.TypeLoadException>.)|
|`public string Source { get; set; }`|Alır ya da uygulama veya hataya neden olan nesnenin adını ayarlar. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string StackTrace { get; }`|Çağrı yığınındaki hemen çerçeveleri dize gösterimini alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|
|`public MethodBase TargetSite { get; }`|Geçerli özel durum oluşturdu yöntemi alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string TypeName { get; ]`|Olan meta verileri eksik türünün tam adını alır. (Devralınan <xref:System.TypeLoadException>.)|

## <a name="methods"></a>Yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|`public bool Equals(Object obj)`|Belirtilen nesnenin geçerli nesneyle eşit olup olmadığını belirler.  (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|
|`protected void Finalize()`|Ücretsiz kaynaklar ve çöp toplamanın alınmadan önce diğer temizleme işlemleri gerçekleştirmesini denemek bir nesne sağlar. (Devralınan <xref:System.Object>.)|
|`public Exception GetBaseException()`|Bir veya daha fazla sonraki özel durumların kök nedenini özel durum verir. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|
|`public int GetHashCode()`|Bir karma kodu döndürür bir `MissingMetadataException` örneği.   (Devralınan <xref:System.Object>.)|
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Ayarlar bir <xref:System.Runtime.Serialization.SerializationInfo> özel durum hakkında bilgi içeren nesne.  (Devralınan <xref:System.TypeLoadException>.)|
|`public Type GetType()`|Geçerli örneğin çalışma zamanı türünü alır. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|
|`protected Object MemberwiseClone()`|Geçerli nesne basit bir kopyasını oluşturur. (Devralınan <xref:System.Object>.)|
|`public string ToString()`|Geçerli özel durumun dize gösterimini döndürür. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|

## <a name="events"></a>Olaylar

|Olay|Açıklama|
|-----------|-----------------|
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Özel durum hakkında veri içeren bir özel durum nesnesi oluşturmak için seri hale getirilmiş bir özel durum serileştirilmiş olduğunda gerçekleşir. (Devralınan <xref:System.Exception?displayProperty=nameWithType>.)|

## <a name="usage-details"></a>Kullanım ayrıntıları

`MissingMetadataException` Yansıma bir derlemede bulunmayan meta verilerine erişmek için kullanıldığında, özel durum harekete geçirilir.

Çalışma zamanında bir uygulama için kullanılabilir meta veri çalışma zamanı yönergeleri (XML yapılandırması) dosyası tarafından tanımlanan *. rd.xml. Bu özel durum gelen uygulamanızı önlemek için değiştirmelisiniz \*. çalışma zamanında bulunması gereken meta verileri tanımlamak için rd.xml. Biçimi hakkında bilgi için \*. rd.xml dosya bkz [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).

> [!IMPORTANT]
> Bu özel durumun, uygulamanızın ihtiyaç duyduğu meta verilerin çalışma zamanında kullanılamaz belirttiğinden, bu özel durum işleme karakteri bir `try` / `catch` blok. Bunun yerine, özel durumun nedenini tanılamak ve çalışma zamanı yönergeleri dosyasını kullanarak kaldırın. Özel durum ortadan kaldırır, çalışma zamanı yönergeleri dosyasına ekleyebilirsiniz girişini almak için iki sorun gidericileri birini kullanabilirsiniz:
>
> - [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/type.html) türleri için.
> - [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/method.html) yöntemleri için.

`MissingMetadataException` Sınıfı benzersiz üye içeriyor; tüm üyelerini kendi temel sınıfından devralınır <xref:System.TypeAccessException>.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Exception?displayProperty=nameWithType>
- <xref:System.TypeAccessException>
- [MissingInteropDataException Sınıfı](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)
- [MissingRuntimeArtifactException Sınıfı](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
