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
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="a587d-103">.NET Framework Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="a587d-103">The .NET Framework Analyzer</span></span>

<span data-ttu-id="a587d-104">.NET Framework tabanlı uygulama kodunuzda olası sorunları bulmak için .NET Framework Çözümleyicisi 'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a587d-104">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="a587d-105">Bu çözümleyici olası sorunları bulur ve bunlara yönelik düzeltmeler önerir.</span><span class="sxs-lookup"><span data-stu-id="a587d-105">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="a587d-106">Çözümleyici, kodunuzu yazarken veya bir CI yapısının parçası olarak Visual Studio 'da etkileşimli olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="a587d-106">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="a587d-107">Geliştirme sürecinde mümkün olduğunca önce Çözümleyicisi projenize eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a587d-107">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="a587d-108">Kodunuzda olası sorunları daha önce bulduklarında, bunları çözmeleri daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="a587d-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="a587d-109">Ancak, bunu geliştirme döngüsüne dilediğiniz zaman ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a587d-109">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="a587d-110">Mevcut kodla ilgili herhangi bir sorunu bulur ve geliştirme yaparken yeni sorunlar hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="a587d-110">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="a587d-111">.NET Framework Çözümleyicisi 'ni yükleme ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a587d-111">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="a587d-112">.NET güvenlik Çözümleyicileri 'nin çalıştırılmasını istediğiniz her projede bir NuGet paketi olarak yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a587d-112">The .NET Security Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="a587d-113">Yalnızca bir geliştiricinin projeye eklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a587d-113">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="a587d-114">Çözümleyici paketi bir proje bağımlılığıdır ve güncelleştirilmiş çözüme sahip olduktan sonra her geliştiricinin makinesinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="a587d-114">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="a587d-115">.NET Framework Çözümleyicisi, [Microsoft. NetFramework. çözümleyiciler](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet paketinde dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="a587d-115">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="a587d-116">Bu paket, güvenlik Çözümleyicileri içeren .NET Framework özgü çözümleyiciler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a587d-116">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="a587d-117">Çoğu durumda, [Microsoft. CodeAnalysis. Fxcopçözümleyiciler](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet paketini isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a587d-117">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span> <span data-ttu-id="a587d-118">Fxcopçözümleyiciler toplu paketi, Framework. çözümleyiciler paketinin yanı sıra aşağıdaki çözümleyiciler için de bulunan tüm çerçeve Çözümleyicileri içerir:</span><span class="sxs-lookup"><span data-stu-id="a587d-118">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>

- <span data-ttu-id="a587d-119">[Microsoft. CodeQuality. çözümleyiciler](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): .NET Standard API 'leri için genel rehberlik ve rehberlik sağlar</span><span class="sxs-lookup"><span data-stu-id="a587d-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="a587d-120">[Microsoft. NetCore. çözümleyiciler](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): .NET Core API 'lerine özgü çözümleyiciler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a587d-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="a587d-121">[Text. çözümleyiciler](https://www.nuget.org/packages/Text.Analyzers): açıklamalar dahil olmak üzere kod olarak içerilen metin için rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="a587d-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="a587d-122">Yüklemek için projeye sağ tıklayın ve "bağımlılıkları Yönet" i seçin.</span><span class="sxs-lookup"><span data-stu-id="a587d-122">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="a587d-123">NuGet Gezgini 'nden "NetFramework çözümleyici" araması yapın veya "FX COP Analyzer" seçeneğini tercih ediyorsanız.</span><span class="sxs-lookup"><span data-stu-id="a587d-123">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="a587d-124">Çözümünüzdeki tüm projelere en son kararlı sürümü yükler.</span><span class="sxs-lookup"><span data-stu-id="a587d-124">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="a587d-125">.NET Framework Çözümleyicisi 'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="a587d-125">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="a587d-126">NuGet paketi yüklendikten sonra çözümünüzü derleyin.</span><span class="sxs-lookup"><span data-stu-id="a587d-126">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="a587d-127">Çözümleyici, kod tabanınızda bulduğu tüm sorunları rapor eder.</span><span class="sxs-lookup"><span data-stu-id="a587d-127">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="a587d-128">Sorunlar, aşağıdaki görüntüde gösterildiği gibi Visual Studio Hata Listesi penceresinde uyarı olarak bildirilir:</span><span class="sxs-lookup"><span data-stu-id="a587d-128">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![Framework Çözümleyicisi tarafından bildirilen sorunlar](./media/framework-analyzers-2.png)

<span data-ttu-id="a587d-130">Kod yazarken, kodunuzda olası bir sorunu dalgalı çizgiler görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="a587d-130">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="a587d-131">Herhangi bir sorunun üzerine gelin ve sorun hakkındaki ayrıntıları ve aşağıdaki görüntüde gösterildiği gibi olası bir düzeltmeyle ilgili önerileri görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="a587d-131">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![Framework çözümleyici tarafından bulunan sorunların etkileşimli raporu](./media/framework-analyzers-1.png)

<span data-ttu-id="a587d-133">Çözümleyiciler çözümünüzdeki kodu inceler ve bu sorunlardan herhangi birine yönelik uyarıların bir listesini sağlar:</span><span class="sxs-lookup"><span data-stu-id="a587d-133">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="a587d-134">CA1058: Türler belli temel türleri genişletmemelidir</span><span class="sxs-lookup"><span data-stu-id="a587d-134">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="a587d-135">.NET Framework doğrudan türetmemelisiniz, çok sayıda tür vardır.</span><span class="sxs-lookup"><span data-stu-id="a587d-135">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span> 

<span data-ttu-id="a587d-136">**Kategori:** Tasarıma</span><span class="sxs-lookup"><span data-stu-id="a587d-136">**Category:** Design</span></span>

<span data-ttu-id="a587d-137">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="a587d-137">**Severity:** Warning</span></span>

<span data-ttu-id="a587d-138">Ek bilgiler: [CA: 1058: türler belirli temel türleri genişletmemelidir](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="a587d-138">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="a587d-139">CA2153: bozuk durum özel durumlarını yakalamayın</span><span class="sxs-lookup"><span data-stu-id="a587d-139">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="a587d-140">Bozuk durum istisnalarını yakalamak hataları (erişim ihlalleri gibi) maskeleyebilir, bu durum tutarsız bir yürütme durumuyla sonuçlanır veya saldırganların bir sistemi tehlikeye atmasına daha kolay hale gelir.</span><span class="sxs-lookup"><span data-stu-id="a587d-140">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="a587d-141">Bunun yerine, daha belirli bir özel durum türleri kümesi yakalayın ve işleyin veya özel durumu yeniden oluşturun</span><span class="sxs-lookup"><span data-stu-id="a587d-141">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="a587d-142">**Kategori:** Güven</span><span class="sxs-lookup"><span data-stu-id="a587d-142">**Category:** Security</span></span>

<span data-ttu-id="a587d-143">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="a587d-143">**Severity:** Warning</span></span>

<span data-ttu-id="a587d-144">Ek bilgi: [# # CA2153: bozuk durum özel durumlarını yakalamayın](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="a587d-144">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="a587d-145">CA2229: Serileştirme oluşturucularını uygulayın</span><span class="sxs-lookup"><span data-stu-id="a587d-145">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="a587d-146"><xref:System.Runtime.Serialization.ISerializable> arabirimini uygulayan ancak gerekli serileştirme oluşturucuyu tanımlamayan bir tür oluşturduğunuzda çözümleyici bu uyarıyı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a587d-146">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="a587d-147">Bu kural ihlalini düzeltmek için seri hale getirme yapıcısını uygular.</span><span class="sxs-lookup"><span data-stu-id="a587d-147">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="a587d-148">Kapalı bir sınıf için kurucusunu özel yapın; aksi takdirde korunmuş yapın.</span><span class="sxs-lookup"><span data-stu-id="a587d-148">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="a587d-149">Serileştirme Oluşturucu aşağıdaki imzaya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a587d-149">The serialization constructor has the following signature:</span></span>

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

<span data-ttu-id="a587d-150">**Kategori:** Kullanımıyla</span><span class="sxs-lookup"><span data-stu-id="a587d-150">**Category:** Usage</span></span>

<span data-ttu-id="a587d-151">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="a587d-151">**Severity:** Warning</span></span>

<span data-ttu-id="a587d-152">Ek bilgi: [CA2229: serileştirme oluşturucuları uygulama](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="a587d-152">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="a587d-153">CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin</span><span class="sxs-lookup"><span data-stu-id="a587d-153">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="a587d-154">Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir.</span><span class="sxs-lookup"><span data-stu-id="a587d-154">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="a587d-155">Bu uyarıyı onarmak için bu alanı açıkça <xref:System.NonSerializedAttribute> işaretlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a587d-155">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="a587d-156">**Kategori:** Kullanımıyla</span><span class="sxs-lookup"><span data-stu-id="a587d-156">**Category:** Usage</span></span>

<span data-ttu-id="a587d-157">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="a587d-157">**Severity:** Warning</span></span>

<span data-ttu-id="a587d-158">Ek bilgi: [CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="a587d-158">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="a587d-159">CA2237: ISerializable türlerini seri hale getirilebilir ile Işaretle</span><span class="sxs-lookup"><span data-stu-id="a587d-159">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="a587d-160">Ortak dil çalışma zamanı tarafından seri hale getirilebilir olarak tanınmak için, türün <xref:System.Runtime.Serialization.ISerializable> arabirimini uygulayarak özel bir serileştirme yordamı kullanması durumunda bile <xref:System.SerializableAttribute> özniteliği kullanılarak işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="a587d-160">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="a587d-161">**Kategori:** Kullanımıyla</span><span class="sxs-lookup"><span data-stu-id="a587d-161">**Category:** Usage</span></span>

<span data-ttu-id="a587d-162">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="a587d-162">**Severity:** Warning</span></span>

<span data-ttu-id="a587d-163">Ek bilgi: [CA2237: ISerializable türlerini seri hale getirilebilir Ile işaretle](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="a587d-163">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="a587d-164">CA3075: XML 'de güvenli olmayan DTD işleme</span><span class="sxs-lookup"><span data-stu-id="a587d-164">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="a587d-165">Güvenli olmayan <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> örnekleri kullanırsanız veya dış varlık kaynaklarına başvuru yaparsanız, ayrıştırıcı güvenilmeyen girişi kabul edebilir ve duyarlı bilgileri saldırganlar 'e açığa çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="a587d-165">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="a587d-166">**Kategori:** Güven</span><span class="sxs-lookup"><span data-stu-id="a587d-166">**Category:** Security</span></span>

<span data-ttu-id="a587d-167">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="a587d-167">**Severity:** Warning</span></span>

<span data-ttu-id="a587d-168">Ek bilgi: [A3075: XML 'de güvenli olmayan DTD işleme](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="a587d-168">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="a587d-169">CA5350: zayıf şifreleme algoritmaları kullanmayın</span><span class="sxs-lookup"><span data-stu-id="a587d-169">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="a587d-170">Saldırı daha gelişmiş hale geldiği için şifreleme algoritmaları zaman içinde azallar.</span><span class="sxs-lookup"><span data-stu-id="a587d-170">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="a587d-171">Bu şifreleme algoritmasının türüne ve uygulamasına bağlı olarak, şifreleme kuvvetinin daha fazla azalmasına izin veren saldırganlar tarafından okunabilen iletileri okuma, şifrelenmiş iletileri okuma, dijital imza, Karma içerikli içerik veya Aksi takdirde, bu algoritmayı temel alan tüm cryptosistemleri tehlikeye atabilir.</span><span class="sxs-lookup"><span data-stu-id="a587d-171">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="a587d-172">Şifreleme için, bir AES algoritması kullanın (AES-256, AES-192 ve AES-128), bir anahtar uzunluğu, 128 bitten büyük veya buna eşit.</span><span class="sxs-lookup"><span data-stu-id="a587d-172">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="a587d-173">Karma için, SHA-2 512 2, SHA-2 384 veya SHA-2 256 gibi bir karma işlevi kullanın.</span><span class="sxs-lookup"><span data-stu-id="a587d-173">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="a587d-174">**Kategori:** Güven</span><span class="sxs-lookup"><span data-stu-id="a587d-174">**Category:** Security</span></span>

<span data-ttu-id="a587d-175">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="a587d-175">**Severity:** Warning</span></span>

<span data-ttu-id="a587d-176">Ek bilgi: [CA5350: zayıf şifreleme algoritmaları kullanmayın](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="a587d-176">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="a587d-177">CA5351: bozuk şifreleme algoritmaları kullanmayın</span><span class="sxs-lookup"><span data-stu-id="a587d-177">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="a587d-178">Bu algoritmanın kesintiye uğramaya uygun hale getirilmesi için bir saldırı vardır.</span><span class="sxs-lookup"><span data-stu-id="a587d-178">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="a587d-179">Bu, saldırganların sağlamak için tasarlanan şifreleme garantilerini kesintiye uğramasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a587d-179">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="a587d-180">Bu şifreleme algoritmasının türüne ve uygulamasına bağlı olarak, saldırganların şifreleme iletilerini okumasına, şifrelenmiş iletilerle müdahale ediyor, dijital imzaları yasaklamasına, karma içerikle müdahale ediyor veya herhangi bir//tr.wikipedia.org/wiki/RSA tabanlı olarak tehlikeye atmasına izin verebilir Bu algoritmada.</span><span class="sxs-lookup"><span data-stu-id="a587d-180">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="a587d-181">Şifreleme için, bir AES algoritması kullanın (AES-256, AES-192 ve AES-128), bir anahtar uzunluğu, 128 bitten büyük veya buna eşit.</span><span class="sxs-lookup"><span data-stu-id="a587d-181">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="a587d-182">Karma için, SHA512 olur, SHA384 veya SHA256 gibi SHA-2 ailesinde bir karma işlev kullanın.</span><span class="sxs-lookup"><span data-stu-id="a587d-182">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="a587d-183">Dijital imzalar için, RSA 'yı 2048 bit veya daha büyük bir anahtar uzunluğunda veya 256 bitten büyük veya buna eşit bir anahtar uzunluğu olan ECDSA kullanın.</span><span class="sxs-lookup"><span data-stu-id="a587d-183">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="a587d-184">**Kategori:** Güven</span><span class="sxs-lookup"><span data-stu-id="a587d-184">**Category:** Security</span></span>

<span data-ttu-id="a587d-185">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="a587d-185">**Severity:** Warning</span></span>

<span data-ttu-id="a587d-186">Ek bilgi: [CA5351: bozuk şifreleme algoritmaları kullanmayın](/visualstudio/code-quality/ca5351)</span><span class="sxs-lookup"><span data-stu-id="a587d-186">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351)</span></span>
