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
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="3da45-103">.NET Framework Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="3da45-103">The .NET Framework Analyzer</span></span>

<span data-ttu-id="3da45-104">.NET Framework tabanlı uygulama kodunuzda olası sorunları bulmak için .NET Framework Çözümleyicisi'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3da45-104">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="3da45-105">Bu çözümleyici olası sorunları ve bunları düzeltmelere önerir bulur.</span><span class="sxs-lookup"><span data-stu-id="3da45-105">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="3da45-106">Çözümleyicisi Visual Studio'da kod yazarken veya CI derleme bir parçası olarak etkileşimli olarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="3da45-106">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="3da45-107">Çözümleyicisi projenize olabildiğince erken geliştirmede eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3da45-107">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="3da45-108">Çabuk kodunuzda olası sorunları bulma, bunlar düzeltmek için daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="3da45-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="3da45-109">Ancak, geliştirme döngüsü herhangi bir zamanda ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3da45-109">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="3da45-110">Herhangi bir sorun var olan kodu bulur ve geliştirme tutmak gibi yeni sorunlar hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="3da45-110">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="3da45-111">Yükleme ve .NET Framework Çözümleyicisi'ni yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3da45-111">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="3da45-112">.NET güvenlik Çözümleyicileri çalışmasını istediğiniz her proje bir NuGet paketi olarak yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3da45-112">The .NET Security Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="3da45-113">Projeye eklemek yalnızca bir geliştirici gerekir.</span><span class="sxs-lookup"><span data-stu-id="3da45-113">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="3da45-114">Çözümleyicisi paketi proje bağımlılığı ve güncelleştirilmiş çözüm olduğunda her geliştiricinin makinesinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="3da45-114">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="3da45-115">.NET Framework Analyzer içinde teslim [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet paketi.</span><span class="sxs-lookup"><span data-stu-id="3da45-115">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="3da45-116">Bu paket, yalnızca belirli çözümleyiciler güvenlik Çözümleyicileri içeren .NET Framework için sağlar.</span><span class="sxs-lookup"><span data-stu-id="3da45-116">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="3da45-117">Çoğu durumda, isteyeceksiniz [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet paketi.</span><span class="sxs-lookup"><span data-stu-id="3da45-117">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span> <span data-ttu-id="3da45-118">FxCopAnalyzers toplama paketi aşağıdaki çözümleyiciler yanı sıra Framework.Analyzers paket dahil tüm framework çözümleyiciler içerir:</span><span class="sxs-lookup"><span data-stu-id="3da45-118">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>
- <span data-ttu-id="3da45-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Genel rehberlik ve standart .NET API'ları için yönergeler sağlar</span><span class="sxs-lookup"><span data-stu-id="3da45-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="3da45-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): çözümleyiciler belirli .NET Core API sağlar.</span><span class="sxs-lookup"><span data-stu-id="3da45-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="3da45-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): yorumlar dahil olmak üzere kod dahil metin yönelik yönergeler sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3da45-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="3da45-122">Yüklemek için projeye sağ tıklayın ve "Bağımlılıkları Yönet" seçin.</span><span class="sxs-lookup"><span data-stu-id="3da45-122">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="3da45-123">NuGet Gezgini'nden "NetFramework Çözümleyicisi" için arama veya tercih ederseniz, "Fx Kopyala Çözümleyicisi".</span><span class="sxs-lookup"><span data-stu-id="3da45-123">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="3da45-124">Çözümünüzdeki tüm projelerdeki en son kararlı sürümü yükleyin.</span><span class="sxs-lookup"><span data-stu-id="3da45-124">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="3da45-125">.NET Framework Çözümleyicisi'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="3da45-125">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="3da45-126">NuGet paketi yüklendikten sonra çözümünüzü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3da45-126">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="3da45-127">Çözümleyicisi temelinizde bulunuyor bulmadığı sorunları rapor eder.</span><span class="sxs-lookup"><span data-stu-id="3da45-127">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="3da45-128">Sorunları aşağıdaki görüntüde gösterildiği gibi Visual Studio hata listesi penceresini uyarı olarak bildirilir:</span><span class="sxs-lookup"><span data-stu-id="3da45-128">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![framework Çözümleyicisi tarafından bildirilen sorunlar](./media/framework-analyzers-2.png)

<span data-ttu-id="3da45-130">Kod yazarken, kodunuzda herhangi bir olası sorun altında dalgalı çizgiler görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="3da45-130">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="3da45-131">Herhangi bir sorun getirin ve aşağıdaki görüntüde gösterildiği gibi sorun ve herhangi bir olası düzeltme yönelik öneriler hakkında ayrıntılar bakın:</span><span class="sxs-lookup"><span data-stu-id="3da45-131">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![Etkileşimli raporun framework Çözümleyicisi tarafından bulunan sorunları](./media/framework-analyzers-1.png)

<span data-ttu-id="3da45-133">Çözümleyiciler çözümünüzdeki kod inceleyin ve herhangi bir bu sorunları için uyarılar bir listesini sağlayın:</span><span class="sxs-lookup"><span data-stu-id="3da45-133">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="3da45-134">CA1058: Türler belli temel türleri genişletmemelidir</span><span class="sxs-lookup"><span data-stu-id="3da45-134">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="3da45-135">.NET Framework'teki yapmanız gereken gelen doğrudan türetilmemiş türleri az sayıda vardır.</span><span class="sxs-lookup"><span data-stu-id="3da45-135">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span> 

<span data-ttu-id="3da45-136">**Kategori:** tasarım</span><span class="sxs-lookup"><span data-stu-id="3da45-136">**Category:** Design</span></span>

<span data-ttu-id="3da45-137">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="3da45-137">**Severity:** Warning</span></span>

<span data-ttu-id="3da45-138">Ek bilgi: [CA:1058: türler belli temel türleri değil genişletmek](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="3da45-138">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="3da45-139">CA2153: bozuk durumda özel durumlarını yakalama değil</span><span class="sxs-lookup"><span data-stu-id="3da45-139">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="3da45-140">Çalýþýrçalýþma yakalama bozuk durumda özel durumları (örneğin, erişim ihlali), yürütme tutarsız bir durumda kaynaklanan veya bir sistem tehdit eden saldırganlara kolaylaştırma hata maske.</span><span class="sxs-lookup"><span data-stu-id="3da45-140">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="3da45-141">Bunun yerine, yakalama ve tanıtıcı daha fazla belirli bir özel durum türleri ayarlayın veya özel durum yeniden oluşturun</span><span class="sxs-lookup"><span data-stu-id="3da45-141">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="3da45-142">**Kategori:** güvenlik</span><span class="sxs-lookup"><span data-stu-id="3da45-142">**Category:** Security</span></span>

<span data-ttu-id="3da45-143">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="3da45-143">**Severity:** Warning</span></span>

<span data-ttu-id="3da45-144">Ek bilgi: [## CA2153: bozuk durumda özel durumlarını yakalama değil](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="3da45-144">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="3da45-145">CA2229: Serileştirme oluşturucularını uygulayın</span><span class="sxs-lookup"><span data-stu-id="3da45-145">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="3da45-146">Uygulayan bir tür oluşturduğunuzda, bu uyarıyı Çözümleyicisi oluşturur <xref:System.Runtime.Serialization.ISerializable> arabirim ancak gerekli serileştirme Oluşturucusu tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="3da45-146">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="3da45-147">Bu kural ihlalini düzeltmek için seri hale getirme yapıcısını uygular.</span><span class="sxs-lookup"><span data-stu-id="3da45-147">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="3da45-148">Kapalı bir sınıf için kurucusunu özel yapın; aksi takdirde korunmuş yapın.</span><span class="sxs-lookup"><span data-stu-id="3da45-148">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="3da45-149">Seri hale getirme oluşturucusu aşağıdaki imzası vardır:</span><span class="sxs-lookup"><span data-stu-id="3da45-149">The serialization constructor has the following signature:</span></span>

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

<span data-ttu-id="3da45-150">**Kategori:** kullanımı</span><span class="sxs-lookup"><span data-stu-id="3da45-150">**Category:** Usage</span></span>

<span data-ttu-id="3da45-151">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="3da45-151">**Severity:** Warning</span></span>

<span data-ttu-id="3da45-152">Ek bilgi: [CA2229: Serileştirme oluşturucularını uygulayın](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="3da45-152">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="3da45-153">CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin</span><span class="sxs-lookup"><span data-stu-id="3da45-153">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="3da45-154">Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir.</span><span class="sxs-lookup"><span data-stu-id="3da45-154">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="3da45-155">Bu alanı açıkça işaretlemelisiniz <xref:System.NonSerializedAttribute> bu uyarıyı çözmek için.</span><span class="sxs-lookup"><span data-stu-id="3da45-155">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="3da45-156">**Kategori:** kullanımı</span><span class="sxs-lookup"><span data-stu-id="3da45-156">**Category:** Usage</span></span>

<span data-ttu-id="3da45-157">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="3da45-157">**Severity:** Warning</span></span>

<span data-ttu-id="3da45-158">Ek bilgi: [CA2235: tüm serileştirilebilir olmayan alanları işaretleyin](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="3da45-158">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="3da45-159">CA2237: ISerializable türleri ile seri hale getirilebilir</span><span class="sxs-lookup"><span data-stu-id="3da45-159">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="3da45-160">Ortak dil çalışma zamanı tarafından seri hale getirilebilir olarak tanınması için türlerini kullanarak işaretlenmelidir <xref:System.SerializableAttribute> bile türü özel seri hale getirme yordamı uygulayarak kullandığında özniteliği <xref:System.Runtime.Serialization.ISerializable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3da45-160">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="3da45-161">**Kategori:** kullanımı</span><span class="sxs-lookup"><span data-stu-id="3da45-161">**Category:** Usage</span></span>

<span data-ttu-id="3da45-162">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="3da45-162">**Severity:** Warning</span></span>

<span data-ttu-id="3da45-163">Ek bilgi: [CA2237: seri hale getirilebilir ile işareti ISerializable türleri](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="3da45-163">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="3da45-164">CA3075: XML işleme güvensiz DTD</span><span class="sxs-lookup"><span data-stu-id="3da45-164">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="3da45-165">Güvenli olmayan kullanırsanız <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> örneği veya giriş ve saldırganlar için hassas bilgileri ifşa güvenilmeyen Dış varlık kaynakları, ayrıştırıcı kabul başvurusu.</span><span class="sxs-lookup"><span data-stu-id="3da45-165">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="3da45-166">**Kategori:** güvenlik</span><span class="sxs-lookup"><span data-stu-id="3da45-166">**Category:** Security</span></span>

<span data-ttu-id="3da45-167">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="3da45-167">**Severity:** Warning</span></span>

<span data-ttu-id="3da45-168">Ek bilgi: [A3075: Güvenli olmayan XML işleme DTD](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="3da45-168">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>


### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="3da45-169">CA5350: zayıf şifreleme algoritmalarına kullanmayın</span><span class="sxs-lookup"><span data-stu-id="3da45-169">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="3da45-170">Saldırıları daha gelişmiş hale gibi şifreleme algoritmaları zamanla düşürebilir.</span><span class="sxs-lookup"><span data-stu-id="3da45-170">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="3da45-171">Tür ve bu şifreleme algoritması uygulamasının bağlı olarak, şifreleme gücünü düşmesine enciphered iletileri okumak, enciphered iletilerle değiştirmesine, dijital imzalar taklit, karma içerikle değiştirmesine saldırganlar daha fazla izin verebilir veya Aksi takdirde bu algoritmadan yola çıkılarak cryptosystem tehlikeye.</span><span class="sxs-lookup"><span data-stu-id="3da45-171">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="3da45-172">Şifreleme için AES algoritması kullanın (AES 256, AES-192 ve AES-128 kabul edilebilir) değerinden büyük veya eşit 128 bit anahtar uzunluğuna sahip.</span><span class="sxs-lookup"><span data-stu-id="3da45-172">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="3da45-173">Karma için karma işlevi olarak SHA-2 512, SHA-2 384 ve SHA-2 256 gibi SHA-2 ailesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3da45-173">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="3da45-174">**Kategori:** güvenlik</span><span class="sxs-lookup"><span data-stu-id="3da45-174">**Category:** Security</span></span>

<span data-ttu-id="3da45-175">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="3da45-175">**Severity:** Warning</span></span>

<span data-ttu-id="3da45-176">Ek bilgi: [CA5350: zayıf şifreleme algoritmalarına kullanmayın](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="3da45-176">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="3da45-177">CA5351: bozuk şifreleme algoritmaları kullanmayın</span><span class="sxs-lookup"><span data-stu-id="3da45-177">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="3da45-178">Bu algoritma bölüneceği bilgisayarlarda mümkündür yapmadan saldırının bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3da45-178">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="3da45-179">Bu, saldırganların sağlamak üzere tasarlanmış şifreleme garanti bölün sağlar.</span><span class="sxs-lookup"><span data-stu-id="3da45-179">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="3da45-180">Türü ve bu şifreleme algoritması uygulamasının bağlı olarak, bu enciphered iletileri okumak, enciphered iletilerle değiştirmesine, dijital imzalar taklit, karma içerikle değiştirmesine veya aksi halde dayalı cryptosystem tehlikeye saldırganların izin Bu algoritma üzerinde.</span><span class="sxs-lookup"><span data-stu-id="3da45-180">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="3da45-181">Şifreleme için AES algoritması kullanın (AES 256, AES-192 ve AES-128 kabul edilebilir) değerinden büyük veya eşit 128 bit anahtar uzunluğuna sahip.</span><span class="sxs-lookup"><span data-stu-id="3da45-181">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="3da45-182">Karma için karma işlevi olarak SHA512, SHA384 veya SHA256 gibi SHA-2 ailesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3da45-182">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="3da45-183">Dijital imzalar için büyük veya ona eşit 256 bit anahtar uzunluğu ile RSA anahtar uzunluğu 2048 bit eşit veya daha büyük ile ya da ECDSA kullanın.</span><span class="sxs-lookup"><span data-stu-id="3da45-183">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="3da45-184">**Kategori:** güvenlik</span><span class="sxs-lookup"><span data-stu-id="3da45-184">**Category:** Security</span></span>

<span data-ttu-id="3da45-185">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="3da45-185">**Severity:** Warning</span></span>

<span data-ttu-id="3da45-186">Ek bilgiler: [CA5351: bozuk şifreleme algoritmaları kullanmayın](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="3da45-186">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span></span>


