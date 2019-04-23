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
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="529d9-103">.NET Framework Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="529d9-103">The .NET Framework Analyzer</span></span>

<span data-ttu-id="529d9-104">.NET Framework tabanlı uygulama kodunuzda olası sorunları bulmak için .NET Framework Çözümleyicisi'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="529d9-104">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="529d9-105">Bu çözümleyici olası sorunlar ve bunları düzeltmeler önerir bulur.</span><span class="sxs-lookup"><span data-stu-id="529d9-105">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="529d9-106">Çözümleyicisi Visual Studio'da kodunuzu yazarken veya bir CI yapısı bir parçası olarak etkileşimli olarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="529d9-106">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="529d9-107">Çözümleyici projenize mümkün olduğunca erken geliştirmede eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="529d9-107">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="529d9-108">Kodunuzdaki olası sorunları çabuk bulun, bunlar düzeltmek için kolaydır.</span><span class="sxs-lookup"><span data-stu-id="529d9-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="529d9-109">Ancak, Geliştirme döngüsünün her zaman ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="529d9-109">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="529d9-110">Varolan kodu herhangi bir sorun bulur ve geliştirme tutmak gibi yeni sorunlar hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="529d9-110">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="529d9-111">Yükleme ve .NET Framework Çözümleyicisi'ni yapılandırma</span><span class="sxs-lookup"><span data-stu-id="529d9-111">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="529d9-112">.NET güvenlik Çözümleyicileri çalışmasını istediğiniz her bir proje üzerinde bir NuGet paketi olarak yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="529d9-112">The .NET Security Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="529d9-113">Yalnızca bir geliştirici projeye eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="529d9-113">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="529d9-114">Çözümleyicisi paket proje bir bağımlılık ve sonra da güncelleştirilen çözümü her geliştiricinin makinede çalışacak.</span><span class="sxs-lookup"><span data-stu-id="529d9-114">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="529d9-115">.NET Framework Çözümleyicisi sunulan [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet paketi.</span><span class="sxs-lookup"><span data-stu-id="529d9-115">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="529d9-116">Bu paket, güvenlik Çözümleyicileri içeren .NET Framework için yalnızca belirli çözümleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="529d9-116">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="529d9-117">Çoğu durumda, bunu istersiniz [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet paketi.</span><span class="sxs-lookup"><span data-stu-id="529d9-117">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span> <span data-ttu-id="529d9-118">FxCopAnalyzers toplam paket Framework.Analyzers paket yanı sıra aşağıdaki Çözümleyicileri dahil tüm framework Çözümleyicileri içerir:</span><span class="sxs-lookup"><span data-stu-id="529d9-118">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>
- <span data-ttu-id="529d9-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Genel rehberlik ve .NET standart API'ler için yönergeler sağlar</span><span class="sxs-lookup"><span data-stu-id="529d9-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="529d9-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Özel çözümleyiciler için .NET Core API'leri sağlar.</span><span class="sxs-lookup"><span data-stu-id="529d9-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="529d9-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Metin açıklama ekleme kodu olarak dahil edilen kılavuzluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="529d9-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="529d9-122">Yüklemek için projeye sağ tıklayın ve "Bağımlılıklar Yönet'i" seçin.</span><span class="sxs-lookup"><span data-stu-id="529d9-122">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="529d9-123">NuGet Gezgini'nden "NetFramework Çözümleyicisi" için arama yapın veya tercih ederseniz, "Fx Cop Çözümleyicisi".</span><span class="sxs-lookup"><span data-stu-id="529d9-123">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="529d9-124">Çözümünüzdeki tüm projelerde en son kararlı sürümünü yükleyin.</span><span class="sxs-lookup"><span data-stu-id="529d9-124">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="529d9-125">.NET Framework Çözümleyicisi'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="529d9-125">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="529d9-126">NuGet paketi yüklendiğinde, çözümünüzü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="529d9-126">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="529d9-127">Kod tabanınızdaki bulan herhangi bir sorun Çözümleyicisi bildirir.</span><span class="sxs-lookup"><span data-stu-id="529d9-127">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="529d9-128">Sorunları aşağıdaki görüntüde gösterildiği gibi Visual Studio Hata Listesi penceresinde, uyarı olarak bildirilir:</span><span class="sxs-lookup"><span data-stu-id="529d9-128">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![framework Çözümleyicisi tarafından bildirilen sorunları](./media/framework-analyzers-2.png)

<span data-ttu-id="529d9-130">Kod yazarken, kodunuzdaki olası sorunları altında dalgalı çizgiler görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="529d9-130">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="529d9-131">Herhangi bir sorun gelin ve aşağıdaki görüntüde gösterildiği gibi sorun ve herhangi bir olası düzeltme önerileri ayrıntılarını görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="529d9-131">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![framework Çözümleyicisi tarafından bulunan sorunları etkileşimli rapor](./media/framework-analyzers-1.png)

<span data-ttu-id="529d9-133">Çözümleyicileri, çözümünüzde kodu inceleyin ve uyarıların bir listesini bu sorunları birini sağlayın:</span><span class="sxs-lookup"><span data-stu-id="529d9-133">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="529d9-134">CA1058: Türler belirli temel türleri aşmamalıdır</span><span class="sxs-lookup"><span data-stu-id="529d9-134">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="529d9-135">Az sayıda .NET Framework'teki yapmanız gereken doğrudan türetilmemiş türleri vardır.</span><span class="sxs-lookup"><span data-stu-id="529d9-135">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span> 

<span data-ttu-id="529d9-136">**Kategori:** Tasarlama</span><span class="sxs-lookup"><span data-stu-id="529d9-136">**Category:** Design</span></span>

<span data-ttu-id="529d9-137">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="529d9-137">**Severity:** Warning</span></span>

<span data-ttu-id="529d9-138">Ek bilgiler: [CA:1058: Türler belirli temel türleri aşmamalıdır](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="529d9-138">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="529d9-139">CA2153: Bozuk durum özel durumları yakalamayın</span><span class="sxs-lookup"><span data-stu-id="529d9-139">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="529d9-140">Çalýþýrçalýþma yakalama bozuk durum özel durumları, yürütme tutarsız bir duruma veya bir sistem tehdit eden saldırganlara kolaylaştırmaya hataları (örneğin, erişim ihlali) gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="529d9-140">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="529d9-141">Bunun yerine, catch ve tutamacı daha fazla belirli bir özel durum türleri ve ayarlamak veya bir özel durum yeniden oluşturun</span><span class="sxs-lookup"><span data-stu-id="529d9-141">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="529d9-142">**Kategori:** Güvenlik</span><span class="sxs-lookup"><span data-stu-id="529d9-142">**Category:** Security</span></span>

<span data-ttu-id="529d9-143">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="529d9-143">**Severity:** Warning</span></span>

<span data-ttu-id="529d9-144">Ek bilgi: [## CA2153: Bozuk durum özel durumları yakalamayın](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="529d9-144">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="529d9-145">CA2229: Serileştirme oluşturucularını uygulayın</span><span class="sxs-lookup"><span data-stu-id="529d9-145">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="529d9-146">Uygulayan bir tür oluştururken Çözümleyicisi bu uyarıyı üretir <xref:System.Runtime.Serialization.ISerializable> arabirim ancak gerekli seri hale getirme oluşturucusunu tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="529d9-146">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="529d9-147">Bu kural ihlalini düzeltmek için seri hale getirme yapıcısını uygular.</span><span class="sxs-lookup"><span data-stu-id="529d9-147">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="529d9-148">Kapalı bir sınıf için kurucusunu özel yapın; aksi takdirde korunmuş yapın.</span><span class="sxs-lookup"><span data-stu-id="529d9-148">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="529d9-149">Seri hale getirme oluşturucusunu şu imzaya sahip:</span><span class="sxs-lookup"><span data-stu-id="529d9-149">The serialization constructor has the following signature:</span></span>

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

<span data-ttu-id="529d9-150">**Kategori:** Kullanım</span><span class="sxs-lookup"><span data-stu-id="529d9-150">**Category:** Usage</span></span>

<span data-ttu-id="529d9-151">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="529d9-151">**Severity:** Warning</span></span>

<span data-ttu-id="529d9-152">Ek bilgiler: [CA2229: Serileştirme oluşturucularını uygulayın](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="529d9-152">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="529d9-153">CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin</span><span class="sxs-lookup"><span data-stu-id="529d9-153">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="529d9-154">Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir.</span><span class="sxs-lookup"><span data-stu-id="529d9-154">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="529d9-155">Bu alanı açıkça işaretlemelisiniz <xref:System.NonSerializedAttribute> bu uyarıyı düzeltmek için.</span><span class="sxs-lookup"><span data-stu-id="529d9-155">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="529d9-156">**Kategori:** Kullanım</span><span class="sxs-lookup"><span data-stu-id="529d9-156">**Category:** Usage</span></span>

<span data-ttu-id="529d9-157">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="529d9-157">**Severity:** Warning</span></span>

<span data-ttu-id="529d9-158">Ek bilgiler: [CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="529d9-158">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="529d9-159">CA2237: Seri hale getirilebilir ile işareti ISerializable türler</span><span class="sxs-lookup"><span data-stu-id="529d9-159">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="529d9-160">Ortak dil çalışma zamanı tarafından seri hale getirilebilir olarak tanınması için türleri kullanılarak işaretlenmelidir <xref:System.SerializableAttribute> bile türü bir özel seri hale getirme yordamı uygulayarak kullandığında özniteliği <xref:System.Runtime.Serialization.ISerializable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="529d9-160">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="529d9-161">**Kategori:** Kullanım</span><span class="sxs-lookup"><span data-stu-id="529d9-161">**Category:** Usage</span></span>

<span data-ttu-id="529d9-162">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="529d9-162">**Severity:** Warning</span></span>

<span data-ttu-id="529d9-163">Ek bilgiler: [CA2237: Seri hale getirilebilir ile işareti ISerializable türler](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="529d9-163">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="529d9-164">CA3075: XML işleme güvensiz DTD</span><span class="sxs-lookup"><span data-stu-id="529d9-164">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="529d9-165">Güvenli olmayan kullanırsanız <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> örnekleri veya giriş ve saldırganlar için hassas bilgileri ifşa güvenilmeyen Dış varlık kaynakları, ayrıştırıcının kabul başvurusu.</span><span class="sxs-lookup"><span data-stu-id="529d9-165">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="529d9-166">**Kategori:** Güvenlik</span><span class="sxs-lookup"><span data-stu-id="529d9-166">**Category:** Security</span></span>

<span data-ttu-id="529d9-167">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="529d9-167">**Severity:** Warning</span></span>

<span data-ttu-id="529d9-168">Ek bilgiler: [A3075: XML işleme güvensiz DTD](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="529d9-168">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="529d9-169">CA5350: Zayıf şifreleme algoritmaları kullanmayın</span><span class="sxs-lookup"><span data-stu-id="529d9-169">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="529d9-170">Şifreleme algoritmaları, saldırıları daha gelişmiş hale olarak zaman içinde düşürebilir.</span><span class="sxs-lookup"><span data-stu-id="529d9-170">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="529d9-171">Tür ve bu şifreleme algoritmasının uygulama bağlı olarak, kendi şifreleme gücünü performansında enciphered iletileri okumak, enciphered iletilerle değiştirmesine, dijital imzalar forge, karma içerikle değiştirmesine saldırganlar daha fazla izin verebilir veya Aksi takdirde bu algoritmadan yola çıkılarak herhangi cryptosystem tehlikeye.</span><span class="sxs-lookup"><span data-stu-id="529d9-171">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="529d9-172">Şifreleme için AES algoritması kullanın (AES-256'yı, AES-192 ve AES-128 kabul edilebilir) büyüktür veya eşittir 128 bit anahtar uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="529d9-172">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="529d9-173">Karma işlevi için bir karma işlevi olarak gibi SHA-2 512, SHA-2 384 ve SHA-2 256, SHA-2 ailesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="529d9-173">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="529d9-174">**Kategori:** Güvenlik</span><span class="sxs-lookup"><span data-stu-id="529d9-174">**Category:** Security</span></span>

<span data-ttu-id="529d9-175">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="529d9-175">**Severity:** Warning</span></span>

<span data-ttu-id="529d9-176">Ek bilgiler: [CA5350: Zayıf şifreleme algoritmaları kullanmayın](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="529d9-176">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="529d9-177">CA5351:: Bozuk şifreleme algoritmaları kullanmayın</span><span class="sxs-lookup"><span data-stu-id="529d9-177">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="529d9-178">Bu algoritma ayırmak için bilgisayarlarda mümkündür yapmadan bir saldırı var.</span><span class="sxs-lookup"><span data-stu-id="529d9-178">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="529d9-179">Bu, saldırganların sağlamak üzere tasarlanmış şifreleme garanti sonu sağlar.</span><span class="sxs-lookup"><span data-stu-id="529d9-179">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="529d9-180">Tür ve bu şifreleme algoritmasının uygulama bağlı olarak, bu enciphered iletileri okumak, enciphered iletilerle değiştirmesine, dijital imzalar forge, karma içerikle değiştirmesine veya aksi halde göre herhangi bir cryptosystem tehlikeye saldırganların izin verebilir Bu algoritmayı.</span><span class="sxs-lookup"><span data-stu-id="529d9-180">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="529d9-181">Şifreleme için AES algoritması kullanın (AES-256'yı, AES-192 ve AES-128 kabul edilebilir) büyüktür veya eşittir 128 bit anahtar uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="529d9-181">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="529d9-182">Karma için SHA-2 ailesindeki SHA512, SHA384 veya SHA256 karma bir işlevi kullanın.</span><span class="sxs-lookup"><span data-stu-id="529d9-182">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="529d9-183">Dijital imzalar için anahtar uzunluğu en az 2048 bit RSA veya ECDSA büyüktür veya eşittir 256 bit anahtar uzunluğu ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="529d9-183">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="529d9-184">**Kategori:** Güvenlik</span><span class="sxs-lookup"><span data-stu-id="529d9-184">**Category:** Security</span></span>

<span data-ttu-id="529d9-185">**Önem derecesi:** Uyarı</span><span class="sxs-lookup"><span data-stu-id="529d9-185">**Severity:** Warning</span></span>

<span data-ttu-id="529d9-186">Ek bilgi: [CA5351:: Bozuk şifreleme algoritmaları kullanmayın](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="529d9-186">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span></span>
