---
title: .NET güvenlik Çözümleyicileri - .NET
description: .NET güvenlik Çözümleyicileri bulmak ve güvenlik riskleri adres için .NET Framework çözümleyiciler paketinde kullanmayı öğrenin
author: billwagner
ms.author: billwagner
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 904218c177ea45f82a73b4532ce3230af954aa85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574627"
---
# <a name="the-net-framework-analyzer"></a>.NET Framework Çözümleyicisi

.NET Framework tabanlı uygulama kodunuzda olası sorunları bulmak için .NET Framework Çözümleyicisi'ni kullanabilirsiniz. Bu çözümleyici olası sorunları ve bunları düzeltmelere önerir bulur.

Çözümleyicisi Visual Studio'da kod yazarken veya CI derleme bir parçası olarak etkileşimli olarak çalıştırır. Çözümleyicisi projenize olabildiğince erken geliştirmede eklemeniz gerekir. Çabuk kodunuzda olası sorunları bulma, bunlar düzeltmek için daha kolaydır. Ancak, geliştirme döngüsü herhangi bir zamanda ekleyebilirsiniz. Herhangi bir sorun var olan kodu bulur ve geliştirme tutmak gibi yeni sorunlar hakkında sizi uyarır.

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>Yükleme ve .NET Framework Çözümleyicisi'ni yapılandırma

.NET güvenlik Çözümleyicileri çalışmasını istediğiniz her proje bir NuGet paketi olarak yüklenmesi gerekir. Projeye eklemek yalnızca bir geliştirici gerekir. Çözümleyicisi paketi proje bağımlılığı ve güncelleştirilmiş çözüm olduğunda her geliştiricinin makinesinde çalışır.

.NET Framework Analyzer içinde teslim [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet paketi. Bu paket, yalnızca belirli çözümleyiciler güvenlik Çözümleyicileri içeren .NET Framework için sağlar. Çoğu durumda, isteyeceksiniz [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet paketi. FxCopAnalyzers toplama paketi aşağıdaki çözümleyiciler yanı sıra Framework.Analyzers paket dahil tüm framework çözümleyiciler içerir:
- [Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Genel rehberlik ve standart .NET API'ları için yönergeler sağlar
- [Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): çözümleyiciler belirli .NET Core API sağlar.
- [Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): yorumlar dahil olmak üzere kod dahil metin yönelik yönergeler sağlanmaktadır.

Yüklemek için projeye sağ tıklayın ve "Bağımlılıkları Yönet" seçin.
NuGet Gezgini'nden "NetFramework Çözümleyicisi" için arama veya tercih ederseniz, "Fx Kopyala Çözümleyicisi". Çözümünüzdeki tüm projelerdeki en son kararlı sürümü yükleyin.

## <a name="using-the-net-framework-analyzer"></a>.NET Framework Çözümleyicisi'ni kullanma

NuGet paketi yüklendikten sonra çözümünüzü oluşturun. Çözümleyicisi temelinizde bulunuyor bulmadığı sorunları rapor eder. Sorunları aşağıdaki görüntüde gösterildiği gibi Visual Studio hata listesi penceresini uyarı olarak bildirilir:

![framework Çözümleyicisi tarafından bildirilen sorunlar](./media/framework-analyzers-2.png)

Kod yazarken, kodunuzda herhangi bir olası sorun altında dalgalı çizgiler görürsünüz.
Herhangi bir sorun getirin ve aşağıdaki görüntüde gösterildiği gibi sorun ve herhangi bir olası düzeltme yönelik öneriler hakkında ayrıntılar bakın:

![Etkileşimli raporun framework Çözümleyicisi tarafından bulunan sorunları](./media/framework-analyzers-1.png)

Çözümleyiciler çözümünüzdeki kod inceleyin ve herhangi bir bu sorunları için uyarılar bir listesini sağlayın:

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Türler belli temel türleri genişletmemelidir

.NET Framework'teki yapmanız gereken gelen doğrudan türetilmemiş türleri az sayıda vardır. 

**Kategori:** tasarım

**Önem derecesi:** Uyarı

Ek bilgi: [CA:1058: türler belli temel türleri değil genişletmek](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153: bozuk durumda özel durumlarını yakalama değil

Çalýþýrçalýþma yakalama bozuk durumda özel durumları (örneğin, erişim ihlali), yürütme tutarsız bir durumda kaynaklanan veya bir sistem tehdit eden saldırganlara kolaylaştırma hata maske. Bunun yerine, yakalama ve tanıtıcı daha fazla belirli bir özel durum türleri ayarlayın veya özel durum yeniden oluşturun

**Kategori:** güvenlik

**Önem derecesi:** Uyarı

Ek bilgi: [## CA2153: bozuk durumda özel durumlarını yakalama değil](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229: Serileştirme oluşturucularını uygulayın

Uygulayan bir tür oluşturduğunuzda, bu uyarıyı Çözümleyicisi oluşturur <xref:System.Runtime.Serialization.ISerializable> arabirim ancak gerekli serileştirme Oluşturucusu tanımlamıyor. Bu kural ihlalini düzeltmek için seri hale getirme yapıcısını uygular. Kapalı bir sınıf için kurucusunu özel yapın; aksi takdirde korunmuş yapın. Seri hale getirme oluşturucusu aşağıdaki imzası vardır:

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

**Kategori:** kullanımı

**Önem derecesi:** Uyarı

Ek bilgi: [CA2229: Serileştirme oluşturucularını uygulayın](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin

Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir. Bu alanı açıkça işaretlemelisiniz <xref:System.NonSerializedAttribute> bu uyarıyı çözmek için.

**Kategori:** kullanımı

**Önem derecesi:** Uyarı

Ek bilgi: [CA2235: tüm serileştirilebilir olmayan alanları işaretleyin](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237: ISerializable türleri ile seri hale getirilebilir

Ortak dil çalışma zamanı tarafından seri hale getirilebilir olarak tanınması için türlerini kullanarak işaretlenmelidir <xref:System.SerializableAttribute> bile türü özel seri hale getirme yordamı uygulayarak kullandığında özniteliği <xref:System.Runtime.Serialization.ISerializable> arabirimi.

**Kategori:** kullanımı

**Önem derecesi:** Uyarı

Ek bilgi: [CA2237: seri hale getirilebilir ile işareti ISerializable türleri](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075: XML işleme güvensiz DTD

Güvenli olmayan kullanırsanız <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> örneği veya giriş ve saldırganlar için hassas bilgileri ifşa güvenilmeyen Dış varlık kaynakları, ayrıştırıcı kabul başvurusu.  

**Kategori:** güvenlik

**Önem derecesi:** Uyarı

Ek bilgi: [A3075: Güvenli olmayan XML işleme DTD](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)


### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: zayıf şifreleme algoritmalarına kullanmayın

Saldırıları daha gelişmiş hale gibi şifreleme algoritmaları zamanla düşürebilir. Tür ve bu şifreleme algoritması uygulamasının bağlı olarak, şifreleme gücünü düşmesine enciphered iletileri okumak, enciphered iletilerle değiştirmesine, dijital imzalar taklit, karma içerikle değiştirmesine saldırganlar daha fazla izin verebilir veya Aksi takdirde bu algoritmadan yola çıkılarak cryptosystem tehlikeye. Şifreleme için AES algoritması kullanın (AES 256, AES-192 ve AES-128 kabul edilebilir) değerinden büyük veya eşit 128 bit anahtar uzunluğuna sahip. Karma için karma işlevi olarak SHA-2 512, SHA-2 384 ve SHA-2 256 gibi SHA-2 ailesini kullanın.

**Kategori:** güvenlik

**Önem derecesi:** Uyarı

Ek bilgi: [CA5350: zayıf şifreleme algoritmalarına kullanmayın](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: bozuk şifreleme algoritmaları kullanmayın

Bu algoritma bölüneceği bilgisayarlarda mümkündür yapmadan saldırının bulunmaktadır. Bu, saldırganların sağlamak üzere tasarlanmış şifreleme garanti bölün sağlar. Türü ve bu şifreleme algoritması uygulamasının bağlı olarak, bu enciphered iletileri okumak, enciphered iletilerle değiştirmesine, dijital imzalar taklit, karma içerikle değiştirmesine veya aksi halde dayalı cryptosystem tehlikeye saldırganların izin Bu algoritma üzerinde. Şifreleme için AES algoritması kullanın (AES 256, AES-192 ve AES-128 kabul edilebilir) değerinden büyük veya eşit 128 bit anahtar uzunluğuna sahip. Karma için karma işlevi olarak SHA512, SHA384 veya SHA256 gibi SHA-2 ailesini kullanın. Dijital imzalar için büyük veya ona eşit 256 bit anahtar uzunluğu ile RSA anahtar uzunluğu 2048 bit eşit veya daha büyük ile ya da ECDSA kullanın.

**Kategori:** güvenlik

**Önem derecesi:** Uyarı

Ek bilgiler: [CA5351: bozuk şifreleme algoritmaları kullanmayın](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)


