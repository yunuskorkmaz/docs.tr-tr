---
title: .NET güvenlik Çözümleyicileri - .NET
description: .NET güvenlik Çözümleyicileri bulmak ve güvenlik riskleri gidermek için .NET Framework Çözümleyicileri paketinde kullanmayı öğrenin
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: cbd9bcdb12a423f54aa4ff82d88f07c20023c48f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769469"
---
# <a name="the-net-framework-analyzer"></a>.NET Framework Çözümleyicisi

.NET Framework tabanlı uygulama kodunuzda olası sorunları bulmak için .NET Framework Çözümleyicisi'ni kullanabilirsiniz. Bu çözümleyici olası sorunlar ve bunları düzeltmeler önerir bulur.

Çözümleyicisi Visual Studio'da kodunuzu yazarken veya bir CI yapısı bir parçası olarak etkileşimli olarak çalıştırır. Çözümleyici projenize mümkün olduğunca erken geliştirmede eklemeniz gerekir. Kodunuzdaki olası sorunları çabuk bulun, bunlar düzeltmek için kolaydır. Ancak, Geliştirme döngüsünün her zaman ekleyebilirsiniz. Varolan kodu herhangi bir sorun bulur ve geliştirme tutmak gibi yeni sorunlar hakkında sizi uyarır.

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>Yükleme ve .NET Framework Çözümleyicisi'ni yapılandırma

.NET güvenlik Çözümleyicileri çalışmasını istediğiniz her bir proje üzerinde bir NuGet paketi olarak yüklenmesi gerekir. Yalnızca bir geliştirici projeye eklemeniz gerekir. Çözümleyicisi paket proje bir bağımlılık ve sonra da güncelleştirilen çözümü her geliştiricinin makinede çalışacak.

.NET Framework Çözümleyicisi sunulan [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet paketi. Bu paket, güvenlik Çözümleyicileri içeren .NET Framework için yalnızca belirli çözümleyicileri sağlar. Çoğu durumda, bunu istersiniz [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet paketi. FxCopAnalyzers toplam paket Framework.Analyzers paket yanı sıra aşağıdaki Çözümleyicileri dahil tüm framework Çözümleyicileri içerir:
- [Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Genel rehberlik ve .NET standart API'ler için yönergeler sağlar
- [Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Özel çözümleyiciler için .NET Core API'leri sağlar.
- [Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Metin açıklama ekleme kodu olarak dahil edilen kılavuzluk sağlar.

Yüklemek için projeye sağ tıklayın ve "Bağımlılıklar Yönet'i" seçin.
NuGet Gezgini'nden "NetFramework Çözümleyicisi" için arama yapın veya tercih ederseniz, "Fx Cop Çözümleyicisi". Çözümünüzdeki tüm projelerde en son kararlı sürümünü yükleyin.

## <a name="using-the-net-framework-analyzer"></a>.NET Framework Çözümleyicisi'ni kullanma

NuGet paketi yüklendiğinde, çözümünüzü oluşturun. Kod tabanınızdaki bulan herhangi bir sorun Çözümleyicisi bildirir. Sorunları aşağıdaki görüntüde gösterildiği gibi Visual Studio Hata Listesi penceresinde, uyarı olarak bildirilir:

![framework Çözümleyicisi tarafından bildirilen sorunları](./media/framework-analyzers-2.png)

Kod yazarken, kodunuzdaki olası sorunları altında dalgalı çizgiler görürsünüz.
Herhangi bir sorun gelin ve aşağıdaki görüntüde gösterildiği gibi sorun ve herhangi bir olası düzeltme önerileri ayrıntılarını görebilirsiniz:

![framework Çözümleyicisi tarafından bulunan sorunları etkileşimli rapor](./media/framework-analyzers-1.png)

Çözümleyicileri, çözümünüzde kodu inceleyin ve uyarıların bir listesini bu sorunları birini sağlayın:

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Türler belirli temel türleri aşmamalıdır

Az sayıda .NET Framework'teki yapmanız gereken doğrudan türetilmemiş türleri vardır. 

**Kategori:** Tasarlama

**Önem derecesi:** Uyarı

Ek bilgiler: [CA:1058: Türler belirli temel türleri aşmamalıdır](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153: Bozuk durum özel durumları yakalamayın

Çalýþýrçalýþma yakalama bozuk durum özel durumları, yürütme tutarsız bir duruma veya bir sistem tehdit eden saldırganlara kolaylaştırmaya hataları (örneğin, erişim ihlali) gizleyebilirsiniz. Bunun yerine, catch ve tutamacı daha fazla belirli bir özel durum türleri ve ayarlamak veya bir özel durum yeniden oluşturun

**Kategori:** Güvenlik

**Önem derecesi:** Uyarı

Ek bilgi: [## CA2153: Bozuk durum özel durumları yakalamayın](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229: Serileştirme oluşturucularını uygulayın

Uygulayan bir tür oluştururken Çözümleyicisi bu uyarıyı üretir <xref:System.Runtime.Serialization.ISerializable> arabirim ancak gerekli seri hale getirme oluşturucusunu tanımlamıyor. Bu kural ihlalini düzeltmek için seri hale getirme yapıcısını uygular. Kapalı bir sınıf için kurucusunu özel yapın; aksi takdirde korunmuş yapın. Seri hale getirme oluşturucusunu şu imzaya sahip:

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

Ek bilgiler: [CA2229: Serileştirme oluşturucularını uygulayın](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin

Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir. Bu alanı açıkça işaretlemelisiniz <xref:System.NonSerializedAttribute> bu uyarıyı düzeltmek için.

**Kategori:** Kullanım

**Önem derecesi:** Uyarı

Ek bilgiler: [CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237: Seri hale getirilebilir ile işareti ISerializable türler

Ortak dil çalışma zamanı tarafından seri hale getirilebilir olarak tanınması için türleri kullanılarak işaretlenmelidir <xref:System.SerializableAttribute> bile türü bir özel seri hale getirme yordamı uygulayarak kullandığında özniteliği <xref:System.Runtime.Serialization.ISerializable> arabirimi.

**Kategori:** Kullanım

**Önem derecesi:** Uyarı

Ek bilgiler: [CA2237: Seri hale getirilebilir ile işareti ISerializable türler](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075: XML işleme güvensiz DTD

Güvenli olmayan kullanırsanız <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> örnekleri veya giriş ve saldırganlar için hassas bilgileri ifşa güvenilmeyen Dış varlık kaynakları, ayrıştırıcının kabul başvurusu.  

**Kategori:** Güvenlik

**Önem derecesi:** Uyarı

Ek bilgiler: [A3075: XML işleme güvensiz DTD](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Zayıf şifreleme algoritmaları kullanmayın

Şifreleme algoritmaları, saldırıları daha gelişmiş hale olarak zaman içinde düşürebilir. Tür ve bu şifreleme algoritmasının uygulama bağlı olarak, kendi şifreleme gücünü performansında enciphered iletileri okumak, enciphered iletilerle değiştirmesine, dijital imzalar forge, karma içerikle değiştirmesine saldırganlar daha fazla izin verebilir veya Aksi takdirde bu algoritmadan yola çıkılarak herhangi cryptosystem tehlikeye. Şifreleme için AES algoritması kullanın (AES-256'yı, AES-192 ve AES-128 kabul edilebilir) büyüktür veya eşittir 128 bit anahtar uzunluğu. Karma işlevi için bir karma işlevi olarak gibi SHA-2 512, SHA-2 384 ve SHA-2 256, SHA-2 ailesini kullanın.

**Kategori:** Güvenlik

**Önem derecesi:** Uyarı

Ek bilgiler: [CA5350: Zayıf şifreleme algoritmaları kullanmayın](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351:: Bozuk şifreleme algoritmaları kullanmayın

Bu algoritma ayırmak için bilgisayarlarda mümkündür yapmadan bir saldırı var. Bu, saldırganların sağlamak üzere tasarlanmış şifreleme garanti sonu sağlar. Tür ve bu şifreleme algoritmasının uygulama bağlı olarak, bu enciphered iletileri okumak, enciphered iletilerle değiştirmesine, dijital imzalar forge, karma içerikle değiştirmesine veya aksi halde göre herhangi bir cryptosystem tehlikeye saldırganların izin verebilir Bu algoritmayı. Şifreleme için AES algoritması kullanın (AES-256'yı, AES-192 ve AES-128 kabul edilebilir) büyüktür veya eşittir 128 bit anahtar uzunluğu. Karma için SHA-2 ailesindeki SHA512, SHA384 veya SHA256 karma bir işlevi kullanın. Dijital imzalar için anahtar uzunluğu en az 2048 bit RSA veya ECDSA büyüktür veya eşittir 256 bit anahtar uzunluğu ile kullanın.

**Kategori:** Güvenlik

**Önem derecesi:** Uyarı

Ek bilgi: [CA5351:: Bozuk şifreleme algoritmaları kullanmayın](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)
