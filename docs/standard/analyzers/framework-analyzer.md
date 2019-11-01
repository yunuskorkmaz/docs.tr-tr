---
title: .NET güvenlik Çözümleyicileri-.NET
description: Güvenlik risklerini bulmak ve çözmek için .NET Framework Çözümleyicileri paketindeki .NET güvenlik çözümleyicilerinin nasıl kullanılacağını öğrenin
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 03268375739b34a43f38c60fbfd2c993da9f3840
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197954"
---
# <a name="the-net-framework-analyzer"></a>.NET Framework Çözümleyicisi

.NET Framework tabanlı uygulama kodunuzda olası sorunları bulmak için .NET Framework Çözümleyicisi 'ni kullanabilirsiniz. Bu çözümleyici olası sorunları bulur ve bunlara yönelik düzeltmeler önerir.

Çözümleyici, kodunuzu yazarken veya bir CI yapısının parçası olarak Visual Studio 'da etkileşimli olarak çalışır. Geliştirme sürecinde mümkün olduğunca önce Çözümleyicisi projenize eklemeniz gerekir. Kodunuzda olası sorunları daha önce bulduklarında, bunları çözmeleri daha kolay olur. Ancak, bunu geliştirme döngüsüne dilediğiniz zaman ekleyebilirsiniz. Mevcut kodla ilgili herhangi bir sorunu bulur ve geliştirme yaparken yeni sorunlar hakkında sizi uyarır.

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>.NET Framework Çözümleyicisi 'ni yükleme ve yapılandırma

.NET güvenlik Çözümleyicileri 'nin çalıştırılmasını istediğiniz her projede bir NuGet paketi olarak yüklenmesi gerekir. Yalnızca bir geliştiricinin projeye eklemesi gerekir. Çözümleyici paketi bir proje bağımlılığıdır ve güncelleştirilmiş çözüme sahip olduktan sonra her geliştiricinin makinesinde çalışır.

.NET Framework Çözümleyicisi, [Microsoft. NetFramework. çözümleyiciler](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet paketinde dağıtılır. Bu paket, güvenlik Çözümleyicileri içeren .NET Framework özgü çözümleyiciler sağlar. Çoğu durumda, [Microsoft. CodeAnalysis. Fxcopçözümleyiciler](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet paketini isteyeceksiniz. Fxcopçözümleyiciler toplu paketi, Framework. çözümleyiciler paketinin yanı sıra aşağıdaki çözümleyiciler için de bulunan tüm çerçeve Çözümleyicileri içerir:

- [Microsoft. CodeQuality. çözümleyiciler](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): .NET Standard API 'leri için genel rehberlik ve rehberlik sağlar
- [Microsoft. NetCore. çözümleyiciler](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): .NET Core API 'lerine özgü çözümleyiciler sağlar.
- [Text. çözümleyiciler](https://www.nuget.org/packages/Text.Analyzers): açıklamalar dahil olmak üzere kod olarak içerilen metin için rehberlik sağlar.

Yüklemek için projeye sağ tıklayın ve "bağımlılıkları Yönet" i seçin.
NuGet Gezgini 'nden "NetFramework çözümleyici" araması yapın veya "FX COP Analyzer" seçeneğini tercih ediyorsanız. Çözümünüzdeki tüm projelere en son kararlı sürümü yükler.

## <a name="using-the-net-framework-analyzer"></a>.NET Framework Çözümleyicisi 'ni kullanma

NuGet paketi yüklendikten sonra çözümünüzü derleyin. Çözümleyici, kod tabanınızda bulduğu tüm sorunları rapor eder. Sorunlar, aşağıdaki görüntüde gösterildiği gibi Visual Studio Hata Listesi penceresinde uyarı olarak bildirilir:

![Framework Çözümleyicisi tarafından bildirilen sorunlar](./media/framework-analyzers-2.png)

Kod yazarken, kodunuzda olası bir sorunu dalgalı çizgiler görürsünüz.
Herhangi bir sorunun üzerine gelin ve sorun hakkındaki ayrıntıları ve aşağıdaki görüntüde gösterildiği gibi olası bir düzeltmeyle ilgili önerileri görürsünüz:

![Framework çözümleyici tarafından bulunan sorunların etkileşimli raporu](./media/framework-analyzers-1.png)

Çözümleyiciler çözümünüzdeki kodu inceler ve bu sorunlardan herhangi birine yönelik uyarıların bir listesini sağlar:

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Türler belli temel türleri genişletmemelidir

.NET Framework doğrudan türetmemelisiniz, çok sayıda tür vardır. 

**Kategori:** Tasarıma

**Önem derecesi:** Uyarı

Ek bilgiler: [CA: 1058: türler belirli temel türleri genişletmemelidir](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153: bozuk durum özel durumlarını yakalamayın

Bozuk durum istisnalarını yakalamak hataları (erişim ihlalleri gibi) maskeleyebilir, bu durum tutarsız bir yürütme durumuyla sonuçlanır veya saldırganların bir sistemi tehlikeye atmasına daha kolay hale gelir. Bunun yerine, daha belirli bir özel durum türleri kümesi yakalayın ve işleyin veya özel durumu yeniden oluşturun

**Kategori:** Güven

**Önem derecesi:** Uyarı

Ek bilgi: [# # CA2153: bozuk durum özel durumlarını yakalamayın](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229: Serileştirme oluşturucularını uygulayın

<xref:System.Runtime.Serialization.ISerializable> arabirimini uygulayan ancak gerekli serileştirme oluşturucuyu tanımlamayan bir tür oluşturduğunuzda çözümleyici bu uyarıyı oluşturur. Bu kural ihlalini düzeltmek için seri hale getirme yapıcısını uygular. Kapalı bir sınıf için kurucusunu özel yapın; aksi takdirde korunmuş yapın. Serileştirme Oluşturucu aşağıdaki imzaya sahiptir:

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

**Kategori:** Kullanımıyla

**Önem derecesi:** Uyarı

Ek bilgi: [CA2229: serileştirme oluşturucuları uygulama](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin

Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir. Bu uyarıyı onarmak için bu alanı açıkça <xref:System.NonSerializedAttribute> işaretlemeniz gerekir.

**Kategori:** Kullanımıyla

**Önem derecesi:** Uyarı

Ek bilgi: [CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237: ISerializable türlerini seri hale getirilebilir ile Işaretle

Ortak dil çalışma zamanı tarafından seri hale getirilebilir olarak tanınmak için, türün <xref:System.Runtime.Serialization.ISerializable> arabirimini uygulayarak özel bir serileştirme yordamı kullanması durumunda bile <xref:System.SerializableAttribute> özniteliği kullanılarak işaretlenmelidir.

**Kategori:** Kullanımıyla

**Önem derecesi:** Uyarı

Ek bilgi: [CA2237: ISerializable türlerini seri hale getirilebilir Ile işaretle](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075: XML 'de güvenli olmayan DTD işleme

Güvenli olmayan <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> örnekleri kullanırsanız veya dış varlık kaynaklarına başvuru yaparsanız, ayrıştırıcı güvenilmeyen girişi kabul edebilir ve duyarlı bilgileri saldırganlar 'e açığa çıkarabilir.  

**Kategori:** Güven

**Önem derecesi:** Uyarı

Ek bilgi: [A3075: XML 'de güvenli olmayan DTD işleme](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: zayıf şifreleme algoritmaları kullanmayın

Saldırı daha gelişmiş hale geldiği için şifreleme algoritmaları zaman içinde azallar. Bu şifreleme algoritmasının türüne ve uygulamasına bağlı olarak, şifreleme kuvvetinin daha fazla azalmasına izin veren saldırganlar tarafından okunabilen iletileri okuma, şifrelenmiş iletileri okuma, dijital imza, Karma içerikli içerik veya Aksi takdirde, bu algoritmayı temel alan tüm cryptosistemleri tehlikeye atabilir. Şifreleme için, bir AES algoritması kullanın (AES-256, AES-192 ve AES-128), bir anahtar uzunluğu, 128 bitten büyük veya buna eşit. Karma için, SHA-2 512 2, SHA-2 384 veya SHA-2 256 gibi bir karma işlevi kullanın.

**Kategori:** Güven

**Önem derecesi:** Uyarı

Ek bilgi: [CA5350: zayıf şifreleme algoritmaları kullanmayın](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: bozuk şifreleme algoritmaları kullanmayın

Bu algoritmanın kesintiye uğramaya uygun hale getirilmesi için bir saldırı vardır. Bu, saldırganların sağlamak için tasarlanan şifreleme garantilerini kesintiye uğramasına olanak tanır. Bu şifreleme algoritmasının türüne ve uygulamasına bağlı olarak, saldırganların şifreleme iletilerini okumasına, şifrelenmiş iletilerle müdahale ediyor, dijital imzaları yasaklamasına, karma içerikle müdahale ediyor veya herhangi bir//tr.wikipedia.org/wiki/RSA tabanlı olarak tehlikeye atmasına izin verebilir Bu algoritmada. Şifreleme için, bir AES algoritması kullanın (AES-256, AES-192 ve AES-128), bir anahtar uzunluğu, 128 bitten büyük veya buna eşit. Karma için, SHA512 olur, SHA384 veya SHA256 gibi SHA-2 ailesinde bir karma işlev kullanın. Dijital imzalar için, RSA 'yı 2048 bit veya daha büyük bir anahtar uzunluğunda veya 256 bitten büyük veya buna eşit bir anahtar uzunluğu olan ECDSA kullanın.

**Kategori:** Güven

**Önem derecesi:** Uyarı

Ek bilgi: [CA5351: bozuk şifreleme algoritmaları kullanmayın](/visualstudio/code-quality/ca5351)
