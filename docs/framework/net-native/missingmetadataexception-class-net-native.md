---
title: MissingMetadataException Sınıfı (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: 408f25c4-6d60-475c-92b1-7b52b777c6db
ms.openlocfilehash: d73d66529bc30358c946eb0a7072f0cb8910b19a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128285"
---
# <a name="missingmetadataexception-class-net-native"></a>MissingMetadataException Sınıfı (.NET Yerel)

**Windows 10 için Windows uygulamaları için .NET, yalnızca .NET Native**

Mevcut olmayan meta verileri almak için yansıma kullanıldığında oluşturulan özel durum.

**Ad alanı:** System. Reflection

> [!IMPORTANT]
> `MissingMetadataException` sınıfı, yalnızca .NET Native araç zinciri tarafından dahili kullanıma yöneliktir. Üçüncü taraf kodda kullanılmak üzere değildir veya uygulama kodunuzda özel durumu işlemelisiniz. Bunun yerine, [çalışma zamanı yönergeleri dosyanıza](runtime-directives-rd-xml-configuration-file-reference.md)girdiler ekleyerek özel durumu ortadan kaldırabilirsiniz. Daha fazla bilgi için, açıklamalar bölümüne bakın.

## <a name="syntax"></a>Sözdizimi

[!code-csharp[ProjectN#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingmetadataexception_syntax1.cs#4)]

`MissingMetadataException` sınıfının <xref:System.TypeAccessException>türediğini unutmayın.

`MissingMetadataException` sınıfı aşağıdaki üyelere sahiptir:

## <a name="constructors"></a>Oluşturucular

|Oluşturucu|Açıklama|
|-----------------|-----------------|
|`public MissingMetadataException()`|Hatayı açıklayan sistem tarafından sağlanan bir ileti kullanarak `MissingMetadataException` sınıfının yeni bir örneğini başlatır.<br /><br /> Bu Oluşturucu yalnızca .NET Native araç zinciri tarafından iç kullanım içindir.|
|`public MissingMetadataException(String message)`|Belirtilen bir hata iletisiyle `MissingMetadataException` sınıfının yeni bir örneğini başlatır.<br /><br /> Bu Oluşturucu yalnızca .NET Native araç zinciri tarafından iç kullanım içindir.|

## <a name="properties"></a>Özellikler

|Özellik|Açıklama|
|--------------|-----------------|
|`public IDictionary Data { get; }`|Özel durum hakkında ek kullanıcı tanımlı bilgiler sağlayan anahtar/değer çiftleri koleksiyonunu alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`public string HelpLink { get; set; }`|Bu özel durumla ilişkili Yardım dosyasının bağlantısını alır veya ayarlar. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`public int HResult { get; protected set; }`|Belirli bir özel duruma atanan kodlanmış sayısal değeri `HRESULT`alır veya ayarlar. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`public Exception InnerException { get; }`|Geçerli özel duruma neden olan özel durumu alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`public string Message { get; }`|Geçerli özel durumu açıklayan bir ileti alır. (<xref:System.TypeLoadException>devralındı.)|
|`public string Source { get; set; }`|Hataya neden olan uygulamanın veya nesnenin adını alır veya ayarlar. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`public string StackTrace { get; }`|Çağrı yığınında anlık çerçevelerin dize gösterimini alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`public MethodBase TargetSite { get; }`|Geçerli özel durumu oluşturan yöntemi alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`public string TypeName { get; ]`|Meta verileri eksik olan türün tam nitelikli adını alır. (<xref:System.TypeLoadException>devralındı.)|

## <a name="methods"></a>Yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|`public bool Equals(Object obj)`|Belirtilen nesnenin geçerli nesneyle eşit olup olmadığını belirler.  (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`protected void Finalize()`|Bir nesnenin çöp toplama tarafından geri alınmadan önce kaynakları serbest bırakma ve diğer temizleme işlemlerini gerçekleştirmesine izin verir. (<xref:System.Object>devralındı.)|
|`public Exception GetBaseException()`|Bir veya daha fazla sonraki özel durumun asıl nedeni olan özel durumu döndürür. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`public int GetHashCode()`|`MissingMetadataException` örneği için bir karma kod döndürür.   (<xref:System.Object>devralındı.)|
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Özel durum hakkında bilgi içeren bir <xref:System.Runtime.Serialization.SerializationInfo> nesnesi ayarlar.  (<xref:System.TypeLoadException>devralındı.)|
|`public Type GetType()`|Geçerli örneğin çalışma zamanı türünü alır. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|
|`protected Object MemberwiseClone()`|Geçerli nesnenin basit bir kopyasını oluşturur. (<xref:System.Object>devralındı.)|
|`public string ToString()`|Geçerli özel durumun dize gösterimini döndürür. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|

## <a name="events"></a>Olaylar

|Olay|Açıklama|
|-----------|-----------------|
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Özel durum hakkında serileştirilmiş veri içeren bir özel durum nesnesi oluşturmak için bir özel durum serileştirildiğinde gerçekleşir. (<xref:System.Exception?displayProperty=nameWithType>devralındı.)|

## <a name="usage-details"></a>Kullanım ayrıntıları

Bir derlemede kullanılamayan meta verilere erişmek için yansıma kullanıldığında `MissingMetadataException` özel durumu oluşturulur.

Çalışma zamanında bir uygulama için kullanılabilen meta veriler, \*. RD. xml çalışma zamanı yönergeleri (XML yapılandırma) dosyası tarafından tanımlanır. Uygulamanızın bu özel durumu oluşturmasını engellemek için, çalışma zamanında bulunması gereken meta verileri tanımlamak üzere \*. RD. xml ' i değiştirmelisiniz. \*. RD. xml dosyasının biçimi hakkında daha fazla bilgi için bkz. [Runtime yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md).

> [!IMPORTANT]
> Bu özel durum, uygulamanız için gereken meta verilerin çalışma zamanında kullanılabilir olmadığını gösterdiği için, bu özel durumu bir `try`/`catch` bloğunda tutamamalısınız. Bunun yerine, özel durumun nedenini tanılamanıza ve bir çalışma zamanı yönergeleri dosyası kullanarak ortadan kaldırmanız gerekir. Özel durumu ortadan kaldıran çalışma zamanı yönergeleri dosyanıza ekleyebileceğiniz girişi almak için iki sorun gidericinin birini kullanabilirsiniz:
>
> - Türler için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/type.html) .
> - Metotlar için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/method.html) .

`MissingMetadataException` sınıfı benzersiz üye içermiyor; tüm üyeleri, <xref:System.TypeAccessException>temel sınıfından devralınır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Exception?displayProperty=nameWithType>
- <xref:System.TypeAccessException>
- [MissingInteropDataException Sınıfı](missinginteropdataexception-class-net-native.md)
- [MissingRuntimeArtifactException Sınıfı](missingruntimeartifactexception-class-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
