---
title: MissingMetadataException Sınıfı (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: 408f25c4-6d60-475c-92b1-7b52b777c6db
ms.openlocfilehash: d73d66529bc30358c946eb0a7072f0cb8910b19a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128285"
---
# <a name="missingmetadataexception-class-net-native"></a>MissingMetadataException Sınıfı (.NET Yerel)

**Windows 10 için Windows uygulamaları için .NET, yalnızca .NET Native**

Mevcut olmayan meta verileri almak için yansıma kullanıldığında oluşturulan özel durum.

**Ad alanı:** System. Reflection

> [!IMPORTANT]
> `MissingMetadataException`Sınıfı yalnızca .NET Native araç zinciri tarafından dahili kullanıma yöneliktir. Üçüncü taraf kodda kullanılmak üzere değildir veya uygulama kodunuzda özel durumu işlemelisiniz. Bunun yerine, [çalışma zamanı yönergeleri dosyanıza](runtime-directives-rd-xml-configuration-file-reference.md)girdiler ekleyerek özel durumu ortadan kaldırabilirsiniz. Daha fazla bilgi için, açıklamalar bölümüne bakın.

## <a name="syntax"></a>Sözdizimi

[!code-csharp[ProjectN#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingmetadataexception_syntax1.cs#4)]

`MissingMetadataException`Sınıfının öğesinden türetildiğine unutmayın <xref:System.TypeAccessException> .

`MissingMetadataException`Sınıfı aşağıdaki üyelere sahiptir:

## <a name="constructors"></a>Oluşturucular

|Oluşturucu|Açıklama|
|-----------------|-----------------|
|`public MissingMetadataException()`|`MissingMetadataException`Hatayı açıklayan sistem tarafından sağlanan bir ileti kullanarak sınıfının yeni bir örneğini başlatır.<br /><br /> Bu Oluşturucu yalnızca .NET Native araç zinciri tarafından iç kullanım içindir.|
|`public MissingMetadataException(String message)`|Belirtilen bir hata iletisiyle sınıfın yeni bir örneğini başlatır `MissingMetadataException` .<br /><br /> Bu Oluşturucu yalnızca .NET Native araç zinciri tarafından iç kullanım içindir.|

## <a name="properties"></a>Özellikler

|Özellik|Açıklama|
|--------------|-----------------|
|`public IDictionary Data { get; }`|Özel durum hakkında ek kullanıcı tanımlı bilgiler sağlayan anahtar/değer çiftleri koleksiyonunu alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|
|`public string HelpLink { get; set; }`|Bu özel durumla ilişkili Yardım dosyasının bağlantısını alır veya ayarlar. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|
|`public int HResult { get; protected set; }`|`HRESULT`Belirli bir özel duruma atanan kodlanmış bir sayısal değeri alır veya ayarlar. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|
|`public Exception InnerException { get; }`|Geçerli özel duruma neden olan özel durumu alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|
|`public string Message { get; }`|Geçerli özel durumu açıklayan bir ileti alır. (Öğesinden devralındı <xref:System.TypeLoadException> .)|
|`public string Source { get; set; }`|Hataya neden olan uygulamanın veya nesnenin adını alır veya ayarlar. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|
|`public string StackTrace { get; }`|Çağrı yığınında anlık çerçevelerin dize gösterimini alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|
|`public MethodBase TargetSite { get; }`|Geçerli özel durumu oluşturan yöntemi alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|
|`public string TypeName { get; ]`|Meta verileri eksik olan türün tam nitelikli adını alır. (Öğesinden devralındı <xref:System.TypeLoadException> .)|

## <a name="methods"></a>Yöntemler

|Yöntem|Açıklama|
|------------|-----------------|
|`public bool Equals(Object obj)`|Belirtilen nesnenin geçerli nesneye eşit olup olmadığını belirler.  (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|
|`protected void Finalize()`|Bir nesnenin çöp toplama tarafından geri alınmadan önce kaynakları serbest bırakma ve diğer temizleme işlemlerini gerçekleştirmesine izin verir. (Öğesinden devralındı <xref:System.Object> .)|
|`public Exception GetBaseException()`|Bir veya daha fazla sonraki özel durumun asıl nedeni olan özel durumu döndürür. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|
|`public int GetHashCode()`|Örnek için bir karma kod döndürür `MissingMetadataException` .   (Öğesinden devralındı <xref:System.Object> .)|
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|<xref:System.Runtime.Serialization.SerializationInfo>Özel durumla ilgili bilgileri içeren bir nesne ayarlar.  (Öğesinden devralındı <xref:System.TypeLoadException> .)|
|`public Type GetType()`|Geçerli örneğin çalışma zamanı türünü alır. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|
|`protected Object MemberwiseClone()`|Geçerli nesnenin basit bir kopyasını oluşturur. (Öğesinden devralındı <xref:System.Object> .)|
|`public string ToString()`|Geçerli özel durumun dize gösterimini döndürür. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|

## <a name="events"></a>Olaylar

|Olay|Açıklama|
|-----------|-----------------|
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Özel durum hakkında serileştirilmiş veri içeren bir özel durum nesnesi oluşturmak için bir özel durum serileştirildiğinde gerçekleşir. (Öğesinden devralındı <xref:System.Exception?displayProperty=nameWithType> .)|

## <a name="usage-details"></a>Kullanım Ayrıntıları

`MissingMetadataException`Özel durum, bir derlemede kullanılamayan meta verilere erişmek için yansıma kullanıldığında oluşturulur.

Çalışma zamanında bir uygulama için kullanılabilen meta veriler, çalışma zamanı yönergeleri (XML yapılandırma) dosyası, \* . RD. xml tarafından tanımlanır. Uygulamanızın bu özel durumu oluşturmasını engellemek için \* . RD. xml ' i, çalışma zamanında bulunması gereken meta verileri tanımlamak için değiştirmelisiniz. . RD. xml dosyasının biçimi hakkında daha fazla bilgi için \* bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md).

> [!IMPORTANT]
> Bu özel durum, uygulamanız için gereken meta verilerin çalışma zamanında kullanılabilir olmadığını gösterdiği için, bu özel durumu bir blokta tutamamalısınız `try` / `catch` . Bunun yerine, özel durumun nedenini tanılamanıza ve bir çalışma zamanı yönergeleri dosyası kullanarak ortadan kaldırmanız gerekir. Özel durumu ortadan kaldıran çalışma zamanı yönergeleri dosyanıza ekleyebileceğiniz girişi almak için iki sorun gidericinin birini kullanabilirsiniz:
>
> - Türler için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/type.html) .
> - Metotlar için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/method.html) .

`MissingMetadataException`Sınıf benzersiz üye içermiyor; tüm üyeleri kendi temel sınıfından devralınır <xref:System.TypeAccessException> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Exception?displayProperty=nameWithType>
- <xref:System.TypeAccessException>
- [MissingInteropDataException Sınıfı](missinginteropdataexception-class-net-native.md)
- [MissingRuntimeArtifactException Sınıfı](missingruntimeartifactexception-class-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
