---
title: .NET güvenlik Çözümleyicileri-.NET
description: Güvenlik risklerini bulmak ve çözmek için .NET Framework Çözümleyicileri paketindeki .NET güvenlik çözümleyicilerinin nasıl kullanılacağını öğrenin
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: da5e72b96fec35404e7e9ae7930f3430143487d2
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929304"
---
# <a name="the-net-framework-analyzer"></a>.NET Framework Çözümleyicisi

.NET Framework tabanlı uygulama kodunuzda olası sorunları bulmak için .NET Framework Çözümleyicisi 'ni kullanabilirsiniz. Bu çözümleyici olası sorunları bulur ve bunlara yönelik düzeltmeler önerir.

Çözümleyici, kodunuzu yazarken veya bir CI yapısının parçası olarak Visual Studio 'da etkileşimli olarak çalışır. Geliştirme sürecinde mümkün olduğunca önce Çözümleyicisi projenize eklemeniz gerekir. Kodunuzda olası sorunları daha önce bulduklarında, bunları çözmeleri daha kolay olur. Ancak, bunu geliştirme döngüsüne dilediğiniz zaman ekleyebilirsiniz. Mevcut kodla ilgili herhangi bir sorunu bulur ve geliştirme yaparken yeni sorunlar hakkında sizi uyarır.

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>.NET Framework Çözümleyicisi 'ni yükleme ve yapılandırma

.NET güvenlik Çözümleyicileri 'nin çalıştırılmasını istediğiniz her projede bir NuGet paketi olarak yüklenmesi gerekir. Yalnızca bir geliştiricinin projeye eklemesi gerekir. Çözümleyici paketi bir proje bağımlılığıdır ve güncelleştirilmiş çözüme sahip olduktan sonra her geliştiricinin makinesinde çalışır.

.NET Framework Çözümleyicisi, [Microsoft. NetFramework. çözümleyiciler](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet paketinde dağıtılır. Bu paket, güvenlik Çözümleyicileri içeren .NET Framework özgü çözümleyiciler sağlar. Çoğu durumda, [Microsoft. CodeAnalysis. Fxcopçözümleyiciler](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet paketini isteyeceksiniz. Fxcopçözümleyiciler toplu paketi, Framework. çözümleyiciler paketinin yanı sıra aşağıdaki çözümleyiciler için de bulunan tüm çerçeve Çözümleyicileri içerir:

- [Microsoft. CodeQuality. çözümleyiciler](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): .NET Standard API 'Leri için genel rehberlik ve rehberlik sağlar
- [Microsoft. NetCore. çözümleyiciler](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): .NET Core API 'Lerine özgü çözümleyiciler sağlar.
- [Metin. çözümleyiciler](https://www.nuget.org/packages/Text.Analyzers): Yorumlar dahil olmak üzere kod olarak içerilen metinler için rehberlik sağlar.

Yüklemek için projeye sağ tıklayın ve "bağımlılıkları Yönet" i seçin.
NuGet Gezgini 'nden "NetFramework çözümleyici" araması yapın veya "FX COP Analyzer" seçeneğini tercih ediyorsanız. Çözümünüzdeki tüm projelere en son kararlı sürümü yükler.

## <a name="using-the-net-framework-analyzer"></a>.NET Framework Çözümleyicisi 'ni kullanma

NuGet paketi yüklendikten sonra çözümünüzü derleyin. Çözümleyici, kod tabanınızda bulduğu tüm sorunları rapor eder. Sorunlar, aşağıdaki görüntüde gösterildiği gibi Visual Studio Hata Listesi penceresinde uyarı olarak bildirilir:

![Framework Çözümleyicisi tarafından bildirilen sorunlar](./media/framework-analyzers-2.png)

Kod yazarken, kodunuzda olası bir sorunu dalgalı çizgiler görürsünüz.
Herhangi bir sorunun üzerine gelin ve sorun hakkındaki ayrıntıları ve aşağıdaki görüntüde gösterildiği gibi olası bir düzeltmeyle ilgili önerileri görürsünüz:

![Framework çözümleyici tarafından bulunan sorunların etkileşimli raporu](./media/framework-analyzers-1.png)

Çözümleyiciler çözümünüzdeki kodu inceler ve bu sorunlardan herhangi birine yönelik uyarıların bir listesini sağlar:

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Türler belirli temel türleri aşmamalıdır

.NET Framework doğrudan türetmemelisiniz, çok sayıda tür vardır. 

**Alan** Tasarlama

**İnin** Uyarı

Ek bilgiler: [CA: 1058: Türler belirli temel türleri genişlememelidir](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153: Bozuk durum özel durumlarını yakalamayın

Bozuk durum istisnalarını yakalamak hataları (erişim ihlalleri gibi) maskeleyebilir, bu durum tutarsız bir yürütme durumuyla sonuçlanır veya saldırganların bir sistemi tehlikeye atmasına daha kolay hale gelir. Bunun yerine, daha belirli bir özel durum türleri kümesi yakalayın ve işleyin veya özel durumu yeniden oluşturun

**Alan** Güvenlik

**İnin** Uyarı

Ek bilgiler: [# # CA2153: Bozuk durum özel durumlarını yakalamayın](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229: Serileştirme oluşturucularını uygulayın

Bu uyarıyı, <xref:System.Runtime.Serialization.ISerializable> arabirimini uygulayan ancak gerekli serileştirme oluşturucusunu tanımlamayan bir tür oluşturduğunuzda oluşturur. Bu kural ihlalini düzeltmek için seri hale getirme yapıcısını uygular. Kapalı bir sınıf için kurucusunu özel yapın; aksi takdirde korunmuş yapın. Serileştirme Oluşturucu aşağıdaki imzaya sahiptir:

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

**Alan** Kullanım

**İnin** Uyarı

Ek bilgiler: [CA2229 Serileştirme oluşturucularını Uygula](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin

Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir. Bu uyarıyı onarmak <xref:System.NonSerializedAttribute> için bu alanı ile açık olarak işaretlemeniz gerekir.

**Alan** Kullanım

**İnin** Uyarı

Ek bilgiler: [CA2235 Tüm seri hale getirilebilir olmayan alanları işaretle](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237: ISerializable türlerini seri hale getirilebilir ile işaretle

Ortak dil çalışma zamanı tarafından seri hale getirilebilir olarak tanınmak için, türün, <xref:System.SerializableAttribute> <xref:System.Runtime.Serialization.ISerializable> arabirimi uygulayarak özel bir serileştirme yordamı kullanması durumunda bile özniteliği kullanılarak işaretlenmesi gerekir.

**Alan** Kullanım

**İnin** Uyarı

Ek bilgiler: [CA2237 ISerializable türlerini seri hale getirilebilir ile işaretle](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075: XML 'de güvenli olmayan DTD işleme

Güvenli olmayan <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> örnekler kullanırsanız veya dış varlık kaynaklarına başvurdıysanız, ayrıştırıcı güvenilmeyen girişi kabul edebilir ve duyarlı bilgileri saldırganlar 'e açığa çıkarabilir.  

**Alan** Güvenlik

**İnin** Uyarı

Ek bilgiler: [A3075: XML 'de güvenli olmayan DTD işleme](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Zayıf şifreleme algoritmaları kullanmayın

Saldırı daha gelişmiş hale geldiği için şifreleme algoritmaları zaman içinde azallar. Bu şifreleme algoritmasının türüne ve uygulamasına bağlı olarak, şifreleme kuvvetinin daha fazla azalmasına izin veren saldırganlar tarafından okunabilen iletileri okuma, şifrelenmiş iletileri okuma, dijital imza, Karma içerikli içerik veya Aksi takdirde, bu algoritmayı temel alan tüm cryptosistemleri tehlikeye atabilir. Şifreleme için, bir AES algoritması kullanın (AES-256, AES-192 ve AES-128), bir anahtar uzunluğu, 128 bitten büyük veya buna eşit. Karma için, SHA-2 512 2, SHA-2 384 veya SHA-2 256 gibi bir karma işlevi kullanın.

**Alan** Güvenlik

**İnin** Uyarı

Ek bilgiler: [CA5350: Zayıf şifreleme algoritmaları kullanmayın](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Bozuk şifreleme algoritmaları kullanmayın

Bu algoritmanın kesintiye uğramaya uygun hale getirilmesi için bir saldırı vardır. Bu, saldırganların sağlamak için tasarlanan şifreleme garantilerini kesintiye uğramasına olanak tanır. Bu şifreleme algoritmasının türüne ve uygulamasına bağlı olarak, saldırganların şifreleme iletilerini okumasına, şifrelenmiş iletilerle müdahale ediyor, dijital imzaları yasaklamasına, karma içerikle müdahale ediyor veya herhangi bir//tr.wikipedia.org/wiki/RSA tabanlı olarak tehlikeye atmasına izin verebilir Bu algoritmada. Şifreleme için, bir AES algoritması kullanın (AES-256, AES-192 ve AES-128), bir anahtar uzunluğu, 128 bitten büyük veya buna eşit. Karma için, SHA512 olur, SHA384 veya SHA256 gibi SHA-2 ailesinde bir karma işlev kullanın. Dijital imzalar için, RSA 'yı 2048 bit veya daha büyük bir anahtar uzunluğunda veya 256 bitten büyük veya buna eşit bir anahtar uzunluğu olan ECDSA kullanın.

**Alan** Güvenlik

**İnin** Uyarı

Ek bilgiler: [CA5351: Bozuk şifreleme algoritmaları kullanmayın](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)
