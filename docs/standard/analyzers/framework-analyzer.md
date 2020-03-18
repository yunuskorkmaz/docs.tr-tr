---
title: .NET Çerçeve Analizörleri - .NET
description: Güvenlik risklerini bulmak ve ele almak için .NET Framework Analyzers paketinde .NET Framework Analyzers'ı nasıl kullanacağınızı öğrenin
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: dd69671e709549fe0ad0f582e4d09b43f7321df2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156003"
---
# <a name="the-net-framework-analyzer"></a>.NET Çerçeve Analizörü

.NET Framework tabanlı uygulama kodunuzda olası sorunları bulmak için .NET Framework Analyzer'ı kullanabilirsiniz. Bu çözümleyici olası sorunları bulur ve bunlara düzeltmeler önerir.

Kodunuzu yazarken veya BIR CI yapısının parçası olarak çözümleyici Visual Studio'da etkileşimli olarak çalışır. Çözümleyiciyi geliştirme aşamasında mümkün olduğunca erken projenize eklemelisiniz. Kodunuzda olası sorunları ne kadar erken bulursanız, bunların düzeltilmesi o kadar kolay olur. Ancak, geliştirme döngüsünde istediğiniz zaman ekleyebilirsiniz. Varolan kodla ilgili herhangi bir sorunu bulur ve siz geliştirmeye devam ettikçe yeni sorunlar hakkında uyarır.

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>.NET Framework Analyzer'ın kurulumu ve yapılandırılması

.NET Framework Analyzers, çalışmasını istediğiniz her projeye NuGet paketi olarak yüklenmelidir. Bunları projeye yalnızca bir geliştirici nin eklemesi gerekir. Çözümleyici paketi bir proje bağımlılığıdır ve güncelleştirilmiş çözüme sahip olduktan sonra her geliştiricinin makinesinde çalışacaktır.

.NET Framework Analyzer [Microsoft.NetFramework.Analyzeers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet paketinde teslim edilir. Bu paket, yalnızca güvenlik çözümleyicilerini içeren .NET Framework'e özgü çözümleyiciler sağlar. Çoğu durumda, [Microsoft.CodeAnalysis.FxCopAnalysisers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet paketini isteyeceksiniz.
FxCopAnalyzers toplu paketi Framework.Analyzers paketinde yer alan tüm çerçeve analizörlerinin yanı sıra aşağıdaki analizörleri de içerir:

- [Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): .NET Standart API'ler için genel kılavuz ve kılavuz sağlar
- [Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): .NET Core API'lerine özgü analizörler sağlar.
- [Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Yorumlar da dahil olmak üzere kod olarak yer alan metin için kılavuzluk sağlar.

Yüklemek için projeye sağ tıklayın ve "Bağımlılıkları Yönet"i seçin.
NuGet gezgininden "NetFramework Analyzer"ı veya "Fx Cop Analyzer"ı tercih ederseniz arayın. Çözümünüzdeki tüm projelerde en son kararlı sürümü yükleyin.

## <a name="using-the-net-framework-analyzer"></a>.NET Framework Analyzer'ı kullanma

NuGet paketi yüklendikten sonra çözümünüzü oluşturun. Çözümleyici, kod tabanınızda bulunduğu sorunları bildirir. Sorunlar, aşağıdaki resimde gösterildiği gibi Visual Studio Hata Listesi penceresinde uyarı olarak bildirilir:

![çerçeve çözümleyicisi tarafından bildirilen sorunlar](./media/framework-analyzers-2.png)

Kod yazarken, kodunuzda herhangi bir olası sorunun altında dalgalı lıklar görürsünüz.
Herhangi bir sorunun üzerine daldığınızda, sorunla ilgili ayrıntıları ve aşağıdaki resimde gösterildiği gibi olası düzeltme önerileri görürsünüz:

![çerçeve çözümleyicisi tarafından bulunan sorunların etkileşimli raporu](./media/framework-analyzers-1.png)

Çözümleyiciler çözümünüzü inceleyen ve bu sorunlardan herhangi biri için uyarıların bir listesini sağlar:

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Türler belli temel türleri genişletmemelidir

.NET Framework'de doğrudan türetilmiş olmamalıdır türleri az sayıda vardır.

**Kategori:** Tasarım

**Önem derecesi:** Uyarı

Ek bilgi: [CA:1058: Türler belirli taban türlerini genişletmemelidir](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153: Bozuk durum özel durumlarını yakalamayın

Bozuk durum özel durumlarını yakalamak hataları (erişim ihlalleri gibi) maskeleyebilir, bu da tutarsız bir yürütme durumuna neden olabilir veya saldırganların bir sistemi tehlikeye atmasını kolaylaştırabilir. Bunun yerine, daha özel bir özel durum türü(ler) kümesini yakalayın ve işleyebilir veya özel durumu yeniden

**Kategori:** Güvenlik

**Önem derecesi:** Uyarı

Ek bilgi: [## CA2153: Bozuk durum özel durumlarını yakalamayın](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229: Serileştirme oluşturucularını uygulayın

Çözümleyici, <xref:System.Runtime.Serialization.ISerializable> arabirimi uygulayan ancak gerekli serioluşturma oluşturucuyu tanımlamayan bir tür oluşturduğunuzda bu uyarıyı oluşturur. Bu kural ihlalini düzeltmek için seri hale getirme yapıcısını uygular. Kapalı bir sınıf için kurucusunu özel yapın; aksi takdirde korunmuş yapın. Serileştirme oluşturucusu aşağıdaki imzaya sahiptir:

```csharp
public class MyItemType
{
    // The special constructor is used to deserialize values.
    public MyItemType(SerializationInfo info, StreamingContext context)
    {
        // implementation removed.
    }
}
```

**Kategori:** Kullanım

**Önem derecesi:** Uyarı

Ek bilgi: [CA2229: Serileştirme oluşturucuları uygulama](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin

Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir. Bu uyarıyı düzeltmek <xref:System.NonSerializedAttribute> için bu alanı açıkça işaretlemeniz gerekir.

**Kategori:** Kullanım

**Önem derecesi:** Uyarı

Ek bilgi: [CA2235: Seri olmayan tüm alanları işaretleyin](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237: Serializable ile Mark ISerializable türleri

Ortak dil çalışma zamanı tarafından serileştirilebilir olarak tanınması için, tür <xref:System.SerializableAttribute> <xref:System.Runtime.Serialization.ISerializable> arabirimi uygulayarak özel bir serileştirme yordamı kullansa bile öznitelik kullanılarak işaretlenmelidir.

**Kategori:** Kullanım

**Önem derecesi:** Uyarı

Ek bilgi: [CA2237: Serializable ile İşaretlenebilir türleri](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075: XML'de güvensiz DTD işleme

Güvenli <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> olmayan örnekler kullanırsanız veya dış varlık kaynaklarına başvurursanız, arayıcı güvenilmeyen girişi kabul edebilir ve hassas bilgileri saldırganlara açıklayabilir.  

**Kategori:** Güvenlik

**Önem derecesi:** Uyarı

Ek bilgi: [A3075: XML'de güvensiz DTD işleme](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Zayıf şifreleme algoritmaları kullanmayın

Saldırılar ilerledikçe şifreleme algoritmaları zamanla bozulur. Bu şifreleme algoritmasının türüne ve uygulamasına bağlı olarak, şifreleme gücünün daha da bozulması saldırganların şifrelenmiş iletileri okumasına, şifrelenmiş iletilerle kurcalamasına, dijital imzalar kurcalanmasına, karma içerikle oynamalarına veya aksi takdirde bu algoritmaya dayalı herhangi bir kripto sistemi tehlikeye. Şifreleme için, anahtar uzunluğu 128 bit'ten büyük veya eşit olan bir AES algoritması (AES-256, AES-192 ve AES-128 kabul edilebilir) kullanın. Karma için SHA-2 512, SHA-2 384 veya SHA-2 256 gibi SHA-2 ailesinde karma işlevi kullanın.

**Kategori:** Güvenlik

**Önem derecesi:** Uyarı

Ek bilgi: [CA5350: Zayıf şifreleme algoritmaları kullanmayın](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Bozuk şifreleme algoritmaları kullanmayın

Bu algoritmayı kırmayı hesaplama açısından mümkün hale getiren bir saldırı var. Bu, saldırganların sağlamak üzere tasarlanmış şifreleme garantilerini kırmalarına olanak tanır. Bu şifreleme algoritmasının türüne ve uygulamasına bağlı olarak, saldırganların şifrelenmiş iletileri okumasına, şifreli iletileri kurcalayıp, dijital imzaları taklit etmesine, karma içerikle kurcalanmasına veya herhangi bir kripto sistemine dayalı olarak tehlikeye atmasını sağlayabilir bu algoritma üzerinde. Şifreleme için, anahtar uzunluğu 128 bit'ten büyük veya eşit olan bir AES algoritması (AES-256, AES-192 ve AES-128 kabul edilebilir) kullanın. Karma için SHA-2 ailesinde SHA512, SHA384 veya SHA256 gibi karma işlevi kullanın. Dijital imzalar için, 2048 bit'ten daha büyük veya eşit anahtar uzunluğuna sahip RSA veya 256 bit'ten daha büyük veya eşit anahtar uzunluğuna sahip ECDSA kullanın.

**Kategori:** Güvenlik

**Önem derecesi:** Uyarı

Ek Bilgi: [CA5351: Bozuk şifreleme algoritmaları kullanmayın](/visualstudio/code-quality/ca5351)
