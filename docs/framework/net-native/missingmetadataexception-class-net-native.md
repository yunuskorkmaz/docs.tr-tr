---
title: MissingMetadataException Sınıfı (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: 408f25c4-6d60-475c-92b1-7b52b777c6db
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb9300917f06ec8e48f2dd412e008efec4dc6917
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941667"
---
# <a name="missingmetadataexception-class-net-native"></a>MissingMetadataException Sınıfı (.NET Yerel)

**Windows 10 için Windows uygulamaları için .NET, yalnızca .NET Native**

Mevcut olmayan meta verileri almak için yansıma kullanıldığında oluşturulan özel durum.

**Uzayına** System. Reflection

> [!IMPORTANT]
> `MissingMetadataException` Sınıfı yalnızca .NET Native araç zinciri tarafından dahili kullanıma yöneliktir. Üçüncü taraf kodda kullanılmak üzere değildir veya uygulama kodunuzda özel durumu işlemelisiniz. Bunun yerine, [çalışma zamanı yönergeleri dosyanıza](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)girdiler ekleyerek özel durumu ortadan kaldırabilirsiniz. Daha fazla bilgi için, açıklamalar bölümüne bakın.

## <a name="syntax"></a>Sözdizimi

[!code-csharp[ProjectN#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingmetadataexception_syntax1.cs#4)]

`MissingMetadataException` Sınıfının öğesinden<xref:System.TypeAccessException>türetildiğine unutmayın.

`MissingMetadataException` Sınıfı aşağıdaki üyelere sahiptir:

## <a name="constructors"></a>Oluşturucular

|Oluşturucu|Açıklama|
|-----------------|-----------------|
|`public MissingMetadataException()`|Hatayı açıklayan sistem tarafından sağlanan bir `MissingMetadataException` ileti kullanarak sınıfının yeni bir örneğini başlatır.<br /><br /> Bu Oluşturucu yalnızca .NET Native araç zinciri tarafından iç kullanım içindir.|
|`public MissingMetadataException(String message)`|Yeni bir örneğini başlatır `MissingMetadataException` belirtilen hata iletisiyle sınıfı.<br /><br /> Bu Oluşturucu yalnızca .NET Native araç zinciri tarafından iç kullanım içindir.|

## <a name="properties"></a>Özellikler

|Özellik|Açıklama|
|--------------|-----------------|
|`public IDictionary Data { get; }`|Özel durum hakkında ek kullanıcı tanımlı bilgiler sağlayan anahtar/değer çiftleri koleksiyonunu alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`public string HelpLink { get; set; }`|Bu özel durumla ilişkili Yardım dosyasının bağlantısını alır veya ayarlar. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`public int HResult { get; protected set; }`|Belirli bir özel duruma `HRESULT`atanan kodlanmış bir sayısal değeri alır veya ayarlar. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`public Exception InnerException { get; }`|Geçerli özel duruma neden olan özel durumu alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`public string Message { get; }`|Geçerli özel durumu açıklayan bir ileti alır. (Öğesinden <xref:System.TypeLoadException>devralındı.)|
|`public string Source { get; set; }`|Hataya neden olan uygulamanın veya nesnenin adını alır veya ayarlar. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`public string StackTrace { get; }`|Çağrı yığınında anlık çerçevelerin dize gösterimini alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`public MethodBase TargetSite { get; }`|Geçerli özel durumu oluşturan yöntemi alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`public string TypeName { get; ]`|Meta verileri eksik olan türün tam nitelikli adını alır. (Öğesinden <xref:System.TypeLoadException>devralındı.)|

## <a name="methods"></a>Yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|`public bool Equals(Object obj)`|Belirtilen nesnenin geçerli nesneyle eşit olup olmadığını belirler.  (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`protected void Finalize()`|Bir nesnenin çöp toplama tarafından geri alınmadan önce kaynakları serbest bırakma ve diğer temizleme işlemlerini gerçekleştirmesine izin verir. (Öğesinden <xref:System.Object>devralındı.)|
|`public Exception GetBaseException()`|Bir veya daha fazla sonraki özel durumun asıl nedeni olan özel durumu döndürür. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`public int GetHashCode()`|`MissingMetadataException` Örnek için bir karma kod döndürür.   (Öğesinden <xref:System.Object>devralındı.)|
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Özel durumla <xref:System.Runtime.Serialization.SerializationInfo> ilgili bilgileri içeren bir nesne ayarlar.  (Öğesinden <xref:System.TypeLoadException>devralındı.)|
|`public Type GetType()`|Geçerli örneğin çalışma zamanı türünü alır. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`protected Object MemberwiseClone()`|Geçerli nesnenin basit bir kopyasını oluşturur. (Öğesinden <xref:System.Object>devralındı.)|
|`public string ToString()`|Geçerli özel durumun dize gösterimini döndürür. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|

## <a name="events"></a>Olaylar

|Olay|Açıklama|
|-----------|-----------------|
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Özel durum hakkında serileştirilmiş veri içeren bir özel durum nesnesi oluşturmak için bir özel durum serileştirildiğinde gerçekleşir. (Öğesinden <xref:System.Exception?displayProperty=nameWithType>devralındı.)|

## <a name="usage-details"></a>Kullanım ayrıntıları

`MissingMetadataException` Özel durum, bir derlemede kullanılamayan meta verilere erişmek için yansıma kullanıldığında oluşturulur.

Çalışma zamanında bir uygulama için kullanılabilen meta veriler, çalışma zamanı yönergeleri (XML yapılandırma) dosyası, \*. RD. xml tarafından tanımlanır. Uygulamanızın bu özel durumu oluşturmasını engellemek için. RD. xml ' \*i, çalışma zamanında bulunması gereken meta verileri tanımlamak için değiştirmelisiniz. \*. RD. xml dosyasının biçimi hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).

> [!IMPORTANT]
> Bu özel durum, uygulamanız için gereken meta verilerin çalışma zamanında kullanılabilir olmadığını gösterdiği için, bu özel durumu bir `try` / `catch` blokta tutamamalısınız. Bunun yerine, özel durumun nedenini tanılamanıza ve bir çalışma zamanı yönergeleri dosyası kullanarak ortadan kaldırmanız gerekir. Özel durumu ortadan kaldıran çalışma zamanı yönergeleri dosyanıza ekleyebileceğiniz girişi almak için iki sorun gidericinin birini kullanabilirsiniz:
>
> - Türler için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/type.html) .
> - Metotlar için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/method.html) .

Sınıf benzersiz üye içermiyor; tüm üyeleri kendi temel <xref:System.TypeAccessException>sınıfından devralınır. `MissingMetadataException`

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Exception?displayProperty=nameWithType>
- <xref:System.TypeAccessException>
- [MissingInteropDataException Sınıfı](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)
- [MissingRuntimeArtifactException Sınıfı](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
