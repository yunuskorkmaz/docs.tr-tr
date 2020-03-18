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
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="0207a-103">.NET Çerçeve Analizörü</span><span class="sxs-lookup"><span data-stu-id="0207a-103">The .NET Framework Analyzer</span></span>

<span data-ttu-id="0207a-104">.NET Framework tabanlı uygulama kodunuzda olası sorunları bulmak için .NET Framework Analyzer'ı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0207a-104">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="0207a-105">Bu çözümleyici olası sorunları bulur ve bunlara düzeltmeler önerir.</span><span class="sxs-lookup"><span data-stu-id="0207a-105">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="0207a-106">Kodunuzu yazarken veya BIR CI yapısının parçası olarak çözümleyici Visual Studio'da etkileşimli olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="0207a-106">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="0207a-107">Çözümleyiciyi geliştirme aşamasında mümkün olduğunca erken projenize eklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="0207a-107">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="0207a-108">Kodunuzda olası sorunları ne kadar erken bulursanız, bunların düzeltilmesi o kadar kolay olur.</span><span class="sxs-lookup"><span data-stu-id="0207a-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="0207a-109">Ancak, geliştirme döngüsünde istediğiniz zaman ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0207a-109">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="0207a-110">Varolan kodla ilgili herhangi bir sorunu bulur ve siz geliştirmeye devam ettikçe yeni sorunlar hakkında uyarır.</span><span class="sxs-lookup"><span data-stu-id="0207a-110">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="0207a-111">.NET Framework Analyzer'ın kurulumu ve yapılandırılması</span><span class="sxs-lookup"><span data-stu-id="0207a-111">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="0207a-112">.NET Framework Analyzers, çalışmasını istediğiniz her projeye NuGet paketi olarak yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="0207a-112">The .NET Framework Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="0207a-113">Bunları projeye yalnızca bir geliştirici nin eklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0207a-113">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="0207a-114">Çözümleyici paketi bir proje bağımlılığıdır ve güncelleştirilmiş çözüme sahip olduktan sonra her geliştiricinin makinesinde çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="0207a-114">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="0207a-115">.NET Framework Analyzer [Microsoft.NetFramework.Analyzeers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet paketinde teslim edilir.</span><span class="sxs-lookup"><span data-stu-id="0207a-115">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="0207a-116">Bu paket, yalnızca güvenlik çözümleyicilerini içeren .NET Framework'e özgü çözümleyiciler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0207a-116">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="0207a-117">Çoğu durumda, [Microsoft.CodeAnalysis.FxCopAnalysisers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet paketini isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0207a-117">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span>
<span data-ttu-id="0207a-118">FxCopAnalyzers toplu paketi Framework.Analyzers paketinde yer alan tüm çerçeve analizörlerinin yanı sıra aşağıdaki analizörleri de içerir:</span><span class="sxs-lookup"><span data-stu-id="0207a-118">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>

- <span data-ttu-id="0207a-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): .NET Standart API'ler için genel kılavuz ve kılavuz sağlar</span><span class="sxs-lookup"><span data-stu-id="0207a-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="0207a-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): .NET Core API'lerine özgü analizörler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0207a-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="0207a-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Yorumlar da dahil olmak üzere kod olarak yer alan metin için kılavuzluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="0207a-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="0207a-122">Yüklemek için projeye sağ tıklayın ve "Bağımlılıkları Yönet"i seçin.</span><span class="sxs-lookup"><span data-stu-id="0207a-122">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="0207a-123">NuGet gezgininden "NetFramework Analyzer"ı veya "Fx Cop Analyzer"ı tercih ederseniz arayın.</span><span class="sxs-lookup"><span data-stu-id="0207a-123">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="0207a-124">Çözümünüzdeki tüm projelerde en son kararlı sürümü yükleyin.</span><span class="sxs-lookup"><span data-stu-id="0207a-124">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="0207a-125">.NET Framework Analyzer'ı kullanma</span><span class="sxs-lookup"><span data-stu-id="0207a-125">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="0207a-126">NuGet paketi yüklendikten sonra çözümünüzü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0207a-126">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="0207a-127">Çözümleyici, kod tabanınızda bulunduğu sorunları bildirir.</span><span class="sxs-lookup"><span data-stu-id="0207a-127">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="0207a-128">Sorunlar, aşağıdaki resimde gösterildiği gibi Visual Studio Hata Listesi penceresinde uyarı olarak bildirilir:</span><span class="sxs-lookup"><span data-stu-id="0207a-128">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![çerçeve çözümleyicisi tarafından bildirilen sorunlar](./media/framework-analyzers-2.png)

<span data-ttu-id="0207a-130">Kod yazarken, kodunuzda herhangi bir olası sorunun altında dalgalı lıklar görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="0207a-130">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="0207a-131">Herhangi bir sorunun üzerine daldığınızda, sorunla ilgili ayrıntıları ve aşağıdaki resimde gösterildiği gibi olası düzeltme önerileri görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="0207a-131">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![çerçeve çözümleyicisi tarafından bulunan sorunların etkileşimli raporu](./media/framework-analyzers-1.png)

<span data-ttu-id="0207a-133">Çözümleyiciler çözümünüzü inceleyen ve bu sorunlardan herhangi biri için uyarıların bir listesini sağlar:</span><span class="sxs-lookup"><span data-stu-id="0207a-133">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="0207a-134">CA1058: Türler belli temel türleri genişletmemelidir</span><span class="sxs-lookup"><span data-stu-id="0207a-134">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="0207a-135">.NET Framework'de doğrudan türetilmiş olmamalıdır türleri az sayıda vardır.</span><span class="sxs-lookup"><span data-stu-id="0207a-135">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span>

<span data-ttu-id="0207a-136">**Kategori:** Tasarım</span><span class="sxs-lookup"><span data-stu-id="0207a-136">**Category:** Design</span></span>

<span data-ttu-id="0207a-137">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="0207a-137">**Severity:** Warning</span></span>

<span data-ttu-id="0207a-138">Ek bilgi: [CA:1058: Türler belirli taban türlerini genişletmemelidir](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="0207a-138">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="0207a-139">CA2153: Bozuk durum özel durumlarını yakalamayın</span><span class="sxs-lookup"><span data-stu-id="0207a-139">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="0207a-140">Bozuk durum özel durumlarını yakalamak hataları (erişim ihlalleri gibi) maskeleyebilir, bu da tutarsız bir yürütme durumuna neden olabilir veya saldırganların bir sistemi tehlikeye atmasını kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="0207a-140">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="0207a-141">Bunun yerine, daha özel bir özel durum türü(ler) kümesini yakalayın ve işleyebilir veya özel durumu yeniden</span><span class="sxs-lookup"><span data-stu-id="0207a-141">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="0207a-142">**Kategori:** Güvenlik</span><span class="sxs-lookup"><span data-stu-id="0207a-142">**Category:** Security</span></span>

<span data-ttu-id="0207a-143">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="0207a-143">**Severity:** Warning</span></span>

<span data-ttu-id="0207a-144">Ek bilgi: [## CA2153: Bozuk durum özel durumlarını yakalamayın](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="0207a-144">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="0207a-145">CA2229: Serileştirme oluşturucularını uygulayın</span><span class="sxs-lookup"><span data-stu-id="0207a-145">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="0207a-146">Çözümleyici, <xref:System.Runtime.Serialization.ISerializable> arabirimi uygulayan ancak gerekli serioluşturma oluşturucuyu tanımlamayan bir tür oluşturduğunuzda bu uyarıyı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0207a-146">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="0207a-147">Bu kural ihlalini düzeltmek için seri hale getirme yapıcısını uygular.</span><span class="sxs-lookup"><span data-stu-id="0207a-147">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="0207a-148">Kapalı bir sınıf için kurucusunu özel yapın; aksi takdirde korunmuş yapın.</span><span class="sxs-lookup"><span data-stu-id="0207a-148">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="0207a-149">Serileştirme oluşturucusu aşağıdaki imzaya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0207a-149">The serialization constructor has the following signature:</span></span>

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

<span data-ttu-id="0207a-150">**Kategori:** Kullanım</span><span class="sxs-lookup"><span data-stu-id="0207a-150">**Category:** Usage</span></span>

<span data-ttu-id="0207a-151">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="0207a-151">**Severity:** Warning</span></span>

<span data-ttu-id="0207a-152">Ek bilgi: [CA2229: Serileştirme oluşturucuları uygulama](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="0207a-152">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="0207a-153">CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin</span><span class="sxs-lookup"><span data-stu-id="0207a-153">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="0207a-154">Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir.</span><span class="sxs-lookup"><span data-stu-id="0207a-154">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="0207a-155">Bu uyarıyı düzeltmek <xref:System.NonSerializedAttribute> için bu alanı açıkça işaretlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0207a-155">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="0207a-156">**Kategori:** Kullanım</span><span class="sxs-lookup"><span data-stu-id="0207a-156">**Category:** Usage</span></span>

<span data-ttu-id="0207a-157">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="0207a-157">**Severity:** Warning</span></span>

<span data-ttu-id="0207a-158">Ek bilgi: [CA2235: Seri olmayan tüm alanları işaretleyin](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="0207a-158">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="0207a-159">CA2237: Serializable ile Mark ISerializable türleri</span><span class="sxs-lookup"><span data-stu-id="0207a-159">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="0207a-160">Ortak dil çalışma zamanı tarafından serileştirilebilir olarak tanınması için, tür <xref:System.SerializableAttribute> <xref:System.Runtime.Serialization.ISerializable> arabirimi uygulayarak özel bir serileştirme yordamı kullansa bile öznitelik kullanılarak işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="0207a-160">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="0207a-161">**Kategori:** Kullanım</span><span class="sxs-lookup"><span data-stu-id="0207a-161">**Category:** Usage</span></span>

<span data-ttu-id="0207a-162">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="0207a-162">**Severity:** Warning</span></span>

<span data-ttu-id="0207a-163">Ek bilgi: [CA2237: Serializable ile İşaretlenebilir türleri](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="0207a-163">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="0207a-164">CA3075: XML'de güvensiz DTD işleme</span><span class="sxs-lookup"><span data-stu-id="0207a-164">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="0207a-165">Güvenli <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> olmayan örnekler kullanırsanız veya dış varlık kaynaklarına başvurursanız, arayıcı güvenilmeyen girişi kabul edebilir ve hassas bilgileri saldırganlara açıklayabilir.</span><span class="sxs-lookup"><span data-stu-id="0207a-165">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="0207a-166">**Kategori:** Güvenlik</span><span class="sxs-lookup"><span data-stu-id="0207a-166">**Category:** Security</span></span>

<span data-ttu-id="0207a-167">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="0207a-167">**Severity:** Warning</span></span>

<span data-ttu-id="0207a-168">Ek bilgi: [A3075: XML'de güvensiz DTD işleme](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="0207a-168">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="0207a-169">CA5350: Zayıf şifreleme algoritmaları kullanmayın</span><span class="sxs-lookup"><span data-stu-id="0207a-169">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="0207a-170">Saldırılar ilerledikçe şifreleme algoritmaları zamanla bozulur.</span><span class="sxs-lookup"><span data-stu-id="0207a-170">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="0207a-171">Bu şifreleme algoritmasının türüne ve uygulamasına bağlı olarak, şifreleme gücünün daha da bozulması saldırganların şifrelenmiş iletileri okumasına, şifrelenmiş iletilerle kurcalamasına, dijital imzalar kurcalanmasına, karma içerikle oynamalarına veya aksi takdirde bu algoritmaya dayalı herhangi bir kripto sistemi tehlikeye.</span><span class="sxs-lookup"><span data-stu-id="0207a-171">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="0207a-172">Şifreleme için, anahtar uzunluğu 128 bit'ten büyük veya eşit olan bir AES algoritması (AES-256, AES-192 ve AES-128 kabul edilebilir) kullanın.</span><span class="sxs-lookup"><span data-stu-id="0207a-172">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="0207a-173">Karma için SHA-2 512, SHA-2 384 veya SHA-2 256 gibi SHA-2 ailesinde karma işlevi kullanın.</span><span class="sxs-lookup"><span data-stu-id="0207a-173">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="0207a-174">**Kategori:** Güvenlik</span><span class="sxs-lookup"><span data-stu-id="0207a-174">**Category:** Security</span></span>

<span data-ttu-id="0207a-175">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="0207a-175">**Severity:** Warning</span></span>

<span data-ttu-id="0207a-176">Ek bilgi: [CA5350: Zayıf şifreleme algoritmaları kullanmayın](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="0207a-176">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="0207a-177">CA5351: Bozuk şifreleme algoritmaları kullanmayın</span><span class="sxs-lookup"><span data-stu-id="0207a-177">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="0207a-178">Bu algoritmayı kırmayı hesaplama açısından mümkün hale getiren bir saldırı var.</span><span class="sxs-lookup"><span data-stu-id="0207a-178">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="0207a-179">Bu, saldırganların sağlamak üzere tasarlanmış şifreleme garantilerini kırmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0207a-179">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="0207a-180">Bu şifreleme algoritmasının türüne ve uygulamasına bağlı olarak, saldırganların şifrelenmiş iletileri okumasına, şifreli iletileri kurcalayıp, dijital imzaları taklit etmesine, karma içerikle kurcalanmasına veya herhangi bir kripto sistemine dayalı olarak tehlikeye atmasını sağlayabilir bu algoritma üzerinde.</span><span class="sxs-lookup"><span data-stu-id="0207a-180">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="0207a-181">Şifreleme için, anahtar uzunluğu 128 bit'ten büyük veya eşit olan bir AES algoritması (AES-256, AES-192 ve AES-128 kabul edilebilir) kullanın.</span><span class="sxs-lookup"><span data-stu-id="0207a-181">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="0207a-182">Karma için SHA-2 ailesinde SHA512, SHA384 veya SHA256 gibi karma işlevi kullanın.</span><span class="sxs-lookup"><span data-stu-id="0207a-182">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="0207a-183">Dijital imzalar için, 2048 bit'ten daha büyük veya eşit anahtar uzunluğuna sahip RSA veya 256 bit'ten daha büyük veya eşit anahtar uzunluğuna sahip ECDSA kullanın.</span><span class="sxs-lookup"><span data-stu-id="0207a-183">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="0207a-184">**Kategori:** Güvenlik</span><span class="sxs-lookup"><span data-stu-id="0207a-184">**Category:** Security</span></span>

<span data-ttu-id="0207a-185">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="0207a-185">**Severity:** Warning</span></span>

<span data-ttu-id="0207a-186">Ek Bilgi: [CA5351: Bozuk şifreleme algoritmaları kullanmayın](/visualstudio/code-quality/ca5351)</span><span class="sxs-lookup"><span data-stu-id="0207a-186">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351)</span></span>
