---
title: Dil bağımsızlığı ve dilden bağımsız bileşenler
description: C#, C++/CLI, F#, IronPython, VB, Visual COBOL ve PowerShell gibi .NET'te desteklenen birçok dilden birinde nasıl geliştirebileceğinizi öğrenin.
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: e1f419dd57c1e90d7ebb57ef572f338a34d1c509
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73423629"
---
# <a name="language-independence-and-language-independent-components"></a><span data-ttu-id="e25a3-103">Dil bağımsızlığı ve dilden bağımsız bileşenler</span><span class="sxs-lookup"><span data-stu-id="e25a3-103">Language independence and language-independent components</span></span>

<span data-ttu-id="e25a3-104">.NET dilden bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-104">.NET is language independent.</span></span> <span data-ttu-id="e25a3-105">Bu, bir geliştirici olarak C#, F#ve Visual Basic gibi .NET uygulamalarını hedefleyen birçok dilden birinde geliştirebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-105">This means that, as a developer, you can develop in one of the many languages that target .NET implementations, such as C#, F#, and Visual Basic.</span></span> <span data-ttu-id="e25a3-106">.NET uygulamaları için geliştirilen sınıf kitaplıklarının türlerine ve üyelerine, orijinal dilin kurallarını izlemeden ve dilin yazıldığı dili bilmek zorunda kalmadan erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-106">You can access the types and members of class libraries developed for .NET implementations without having to know the language in which they were originally written and without having to follow any of the original language's conventions.</span></span> <span data-ttu-id="e25a3-107">Bileşen geliştiricisiyseniz, bileşeninize dili ne olursa olsun herhangi bir .NET uygulaması erişebilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-107">If you are a component developer, your component can be accessed by any .NET app regardless of its language.</span></span>

> [!NOTE]
> <span data-ttu-id="e25a3-108">Bu makalenin bu ilk bölümünde, dilden bağımsız bileşenler - yani herhangi bir dilde yazılmış uygulamalar tarafından tüketilebilen bileşenler oluşturma yı tartışır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-108">This first part of this article discusses creating language-independent components - that is, components that can be consumed by apps that are written in any language.</span></span> <span data-ttu-id="e25a3-109">Ayrıca, birden çok dilde yazılmış kaynak kodundan tek bir bileşen veya uygulama oluşturabilirsiniz; bu makalenin ikinci bölümünde [Çapraz Diller Arası Birlikte çalışabilirlik](#cross-language-interoperability) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e25a3-109">You can also create a single component or app from source code written in multiple languages; see [Cross-Language Interoperability](#cross-language-interoperability) in the second part of this article.</span></span>

<span data-ttu-id="e25a3-110">Herhangi bir dilde yazılmış diğer nesnelerle tam olarak etkileşimde kalmak için, nesnelerin arayanlara yalnızca tüm dillerde ortak olan bu özellikleri ortaya çıkarmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-110">To fully interact with other objects written in any language, objects must expose to callers only those features that are common to all languages.</span></span> <span data-ttu-id="e25a3-111">Bu yaygın özellik kümesi, oluşturulan derlemeler için geçerli olan bir kural kümesi olan Ortak Dil Belirtimi (CLS) tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-111">This common set of features is defined by the Common Language Specification (CLS), which is a set of rules that apply to generated assemblies.</span></span> <span data-ttu-id="e25a3-112">Ortak Dil Belirtimi Bölüm I, Clauses 7 ile 11 [ECMA-335 Standart: Ortak Dil Altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm)tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-112">The Common Language Specification is defined in Partition I, Clauses 7 through 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>

<span data-ttu-id="e25a3-113">Bileşeniniz Ortak Dil Belirtimi'ne uygunsa, CLS uyumlu olduğu garanti edilir ve CLS'yi destekleyen herhangi bir programlama dilinde yazılmış derlemelerde koddan erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-113">If your component conforms to the Common Language Specification, it is guaranteed to be CLS-compliant and can be accessed from code in assemblies written in any programming language that supports the CLS.</span></span> <span data-ttu-id="e25a3-114">[ClSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliğini kaynak kodunuza uygulayarak bileşeninizin derleme zamanında Ortak Dil Belirtimine uygun olup olmadığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-114">You can determine whether your component conforms to the Common Language Specification at compile time by applying the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute to your source code.</span></span> <span data-ttu-id="e25a3-115">Daha fazla bilgi için [CLSCompliant Attribute özniteliğine](#the-clscompliantattribute-attribute)bakın.</span><span class="sxs-lookup"><span data-stu-id="e25a3-115">For more information, see The [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute).</span></span>

<span data-ttu-id="e25a3-116">Bu makalede:</span><span class="sxs-lookup"><span data-stu-id="e25a3-116">In this article:</span></span>

* [<span data-ttu-id="e25a3-117">CLS uyumluluk kuralları</span><span class="sxs-lookup"><span data-stu-id="e25a3-117">CLS compliance rules</span></span>](#cls-compliance-rules)

  * [<span data-ttu-id="e25a3-118">Üye imzatürleri ve türleri</span><span class="sxs-lookup"><span data-stu-id="e25a3-118">Types and type member signatures</span></span>](#types-and-type-member-signatures)

  * [<span data-ttu-id="e25a3-119">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="e25a3-119">Naming conventions</span></span>](#naming-conventions)

  * [<span data-ttu-id="e25a3-120">Tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e25a3-120">Type conversion</span></span>](#type-conversion)

  * [<span data-ttu-id="e25a3-121">Diziler</span><span class="sxs-lookup"><span data-stu-id="e25a3-121">Arrays</span></span>](#arrays)

  * [<span data-ttu-id="e25a3-122">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="e25a3-122">Interfaces</span></span>](#interfaces)

  * [<span data-ttu-id="e25a3-123">Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="e25a3-123">Enumerations</span></span>](#enumerations)

  * [<span data-ttu-id="e25a3-124">Genel olarak tip üyeleri</span><span class="sxs-lookup"><span data-stu-id="e25a3-124">Type members in general</span></span>](#type-members-in-general)

  * [<span data-ttu-id="e25a3-125">Üye erişilebilirliği</span><span class="sxs-lookup"><span data-stu-id="e25a3-125">Member accessibility</span></span>](#member-accessibility)

  * [<span data-ttu-id="e25a3-126">Genel türler ve üyeler</span><span class="sxs-lookup"><span data-stu-id="e25a3-126">Generic types and members</span></span>](#generic-types-and-members)

  * [<span data-ttu-id="e25a3-127">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="e25a3-127">Constructors</span></span>](#constructors)

  * [<span data-ttu-id="e25a3-128">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-128">Properties</span></span>](#properties)

  * [<span data-ttu-id="e25a3-129">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e25a3-129">Events</span></span>](#events)

  * [<span data-ttu-id="e25a3-130">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="e25a3-130">Overloads</span></span>](#overloads)

  * [<span data-ttu-id="e25a3-131">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="e25a3-131">Exceptions</span></span>](#exceptions)

  * [<span data-ttu-id="e25a3-132">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-132">Attributes</span></span>](#attributes)

* [<span data-ttu-id="e25a3-133">CLSCompliantAttribute özniteliği</span><span class="sxs-lookup"><span data-stu-id="e25a3-133">CLSCompliantAttribute attribute</span></span>](#the-clscompliantattribute-attribute)

* [<span data-ttu-id="e25a3-134">Diller Arası Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="e25a3-134">Cross-Language Interoperability</span></span>](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a><span data-ttu-id="e25a3-135">CLS uyumluluk kuralları</span><span class="sxs-lookup"><span data-stu-id="e25a3-135">CLS compliance rules</span></span>

<span data-ttu-id="e25a3-136">Bu bölümde CLS uyumlu bir bileşen oluşturma kuralları tartışılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-136">This section discusses the rules for creating a CLS-compliant component.</span></span> <span data-ttu-id="e25a3-137">Kuralların tam listesi için, [ECMA-335 Standardının](https://www.ecma-international.org/publications/standards/Ecma-335.htm)Bölüm I, Madde 11: Ortak Dil Altyapısı'na bakın.</span><span class="sxs-lookup"><span data-stu-id="e25a3-137">For a complete list of rules, see Partition I, Clause 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>

> [!NOTE]
> <span data-ttu-id="e25a3-138">Ortak Dil Belirtimi, tüketiciler (CLS uyumlu bir bileşene programlı olarak erişen geliştiriciler), çerçeveler (oluşturmak için bir dil derleyicisi kullanan geliştiriciler) için geçerli olduğu için CLS uyumluluğu için her kuralı tartışır CLS uyumlu kitaplıklar ve genişleticiler (dil derleyicisi veya CLS uyumlu bileşenler oluşturan bir kod aracı gibi bir araç oluşturan geliştiriciler).</span><span class="sxs-lookup"><span data-stu-id="e25a3-138">The Common Language Specification discusses each rule for CLS compliance as it applies to consumers (developers who are programmatically accessing a component that is CLS-compliant), frameworks (developers who are using a language compiler to create CLS-compliant libraries), and extenders (developers who are creating a tool such as a language compiler or a code parser that creates CLS-compliant components).</span></span> <span data-ttu-id="e25a3-139">Bu makalede, çerçeveler için geçerli olarak kurallar üzerinde duruluyor.</span><span class="sxs-lookup"><span data-stu-id="e25a3-139">This article focuses on the rules as they apply to frameworks.</span></span> <span data-ttu-id="e25a3-140">Ancak, genişleticiler için geçerli olan bazı kuralların [Reflection.Emit](xref:System.Reflection.Emit)kullanılarak oluşturulan derlemeler için de geçerli olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e25a3-140">Note, though, that some of the rules that apply to extenders may also apply to assemblies that are created using [Reflection.Emit](xref:System.Reflection.Emit).</span></span>

<span data-ttu-id="e25a3-141">Dilden bağımsız bir bileşen tasarlamak için CLS uyumluluğu kurallarını bileşeninizin ortak arabirimine uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-141">To design a component that is language independent, you only need to apply the rules for CLS compliance to your component's public interface.</span></span> <span data-ttu-id="e25a3-142">Özel uygulamanız belirtime uymak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-142">Your private implementation does not have to conform to the specification.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e25a3-143">CLS uyumluluğu için kurallar, özel uygulaması için değil, yalnızca bir bileşenin ortak arabirimi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-143">The rules for CLS compliance apply only to a component's public interface, not to its private implementation.</span></span>

<span data-ttu-id="e25a3-144">Örneğin, [Byte](xref:System.Byte) dışındaki imzasız tümerler CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-144">For example, unsigned integers other than [Byte](xref:System.Byte) are not CLS-compliant.</span></span> <span data-ttu-id="e25a3-145">Aşağıdaki `Person` örnekteki sınıf `Age` [UInt16](xref:System.UInt16)türüözelliğini ortaya çıkardığından, aşağıdaki kod derleyici uyarısı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e25a3-145">Because the `Person` class in the following example exposes an `Age` property of type [UInt16](xref:System.UInt16), the following code displays a compiler warning.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private UInt16 personAge = 0;

   public UInt16 Age
   { get { return personAge; } }
}
// The attempt to compile the example displays the following compiler warning:
//    Public1.cs(10,18): warning CS3003: Type of 'Person.Age' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As UInt16
      Get
         Return personAge
      End Get
   End Property
End Class
' The attempt to compile the example displays the following compiler warning:
'    Public1.vb(9) : warning BC40027: Return type of function 'Age' is not CLS-compliant.
'
'       Public ReadOnly Property Age As UInt16
'                                ~~~
```

<span data-ttu-id="e25a3-146">ClS uyumlu, 16 bit imzalı bir `Age` tamsayı `UInt16` olan [Int16](xref:System.Int16)özelliğinin türünü değiştirerek Kişi sınıfı CLS uyumlu hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-146">You can make the Person class CLS-compliant by changing the type of `Age` property from `UInt16` to [Int16](xref:System.Int16), which is a CLS-compliant, 16-bit signed integer.</span></span> <span data-ttu-id="e25a3-147">Özel `personAge` alanın türünü değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e25a3-147">You do not have to change the type of the private `personAge` field.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private Int16 personAge = 0;

   public Int16 Age
   { get { return personAge; } }
}
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As Int16
      Get
         Return CType(personAge, Int16)
      End Get
   End Property
End Class
```

<span data-ttu-id="e25a3-148">Bir kitaplığın ortak arabirimi aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="e25a3-148">A library's public interface consists of the following:</span></span>

* <span data-ttu-id="e25a3-149">Ortak sınıfların tanımları.</span><span class="sxs-lookup"><span data-stu-id="e25a3-149">Definitions of public classes.</span></span>

* <span data-ttu-id="e25a3-150">Ortak sınıfların genel üyelerinin tanımları ve türemiş sınıflara erişilebilen üyelerin tanımları (diğer bir şekilde korunan üyeler).</span><span class="sxs-lookup"><span data-stu-id="e25a3-150">Definitions of the public members of public classes, and definitions of members accessible to derived classes (that is, protected members).</span></span>

* <span data-ttu-id="e25a3-151">Genel sınıfların ortak yöntemlerinin parametreleri ve dönüş türleri ile türemiş sınıflar için erişilebilir parametreler ve dönüş yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="e25a3-151">Parameters and return types of public methods of public classes, and parameters and return types of methods accessible to derived classes.</span></span>

<span data-ttu-id="e25a3-152">CLS uyumluluk kuralları aşağıdaki tabloda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-152">The rules for CLS compliance are listed in the following table.</span></span> <span data-ttu-id="e25a3-153">Kuralların metni [ECMA-335 Standardı: Ortak Dil Altyapısından,](https://www.ecma-international.org/publications/standards/Ecma-335.htm)Telif Hakkı 2012 Ecma International tarafından aynen alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-153">The text of the rules is taken verbatim from the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), which is Copyright 2012 by Ecma International.</span></span> <span data-ttu-id="e25a3-154">Bu kurallar hakkında daha ayrıntılı bilgi aşağıdaki bölümlerde yer aldı.</span><span class="sxs-lookup"><span data-stu-id="e25a3-154">More detailed information about these rules is found in the following sections.</span></span>

<span data-ttu-id="e25a3-155">Kategori</span><span class="sxs-lookup"><span data-stu-id="e25a3-155">Category</span></span> | <span data-ttu-id="e25a3-156">Bkz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-156">See</span></span> | <span data-ttu-id="e25a3-157">Kural</span><span class="sxs-lookup"><span data-stu-id="e25a3-157">Rule</span></span> | <span data-ttu-id="e25a3-158">Kural Numarası</span><span class="sxs-lookup"><span data-stu-id="e25a3-158">Rule Number</span></span>
-------- | --- | ---- | -----------
<span data-ttu-id="e25a3-159">Erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="e25a3-159">Accessibility</span></span> | [<span data-ttu-id="e25a3-160">Üye erişilebilirliği</span><span class="sxs-lookup"><span data-stu-id="e25a3-160">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="e25a3-161">Erişilebilirlik, erişilebilirlik `family-or-assembly`ile farklı bir derlemeden devralınan bir yöntemi geçersiz kılmak dışında, devralınan yöntemleri geçersiz kılarak erişilebilirlik değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="e25a3-161">Accessibility shall not be changed when overriding inherited methods, except when overriding a method inherited from a different assembly with accessibility `family-or-assembly`.</span></span> <span data-ttu-id="e25a3-162">Bu durumda, geçersiz kılma erişilebilirlik `family`olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-162">In this case, the override shall have accessibility `family`.</span></span> | <span data-ttu-id="e25a3-163">10</span><span class="sxs-lookup"><span data-stu-id="e25a3-163">10</span></span>
<span data-ttu-id="e25a3-164">Erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="e25a3-164">Accessibility</span></span> | [<span data-ttu-id="e25a3-165">Üye erişilebilirliği</span><span class="sxs-lookup"><span data-stu-id="e25a3-165">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="e25a3-166">Türlerin ve üyelerin görünürlüğü ve erişilebilirliği, herhangi bir üyenin imzasındaki türlerin görünür ve erişilebilir olması durumunda görünür ve erişilebilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-166">The visibility and accessibility of types and members shall be such that types in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="e25a3-167">Örneğin, derlemesi dışında görünen genel bir yöntem, türü yalnızca derleme içinde görünen bir bağımsız değişkene sahip olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-167">For example, a public method that is visible outside its assembly shall not have an argument whose type is visible only within the assembly.</span></span> <span data-ttu-id="e25a3-168">Herhangi bir üyenin imzasında kullanılan anlık genel bir türü oluşturan türlerin görünürlüğü ve erişilebilirliği, üyenin kendisi görünür ve erişilebilir olduğunda görünür ve erişilebilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-168">The visibility and accessibility of types composing an instantiated generic type used in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="e25a3-169">Örneğin, derlemesi dışında görünen bir üyenin imzasında bulunan anlık genel bir tür, türü yalnızca derleme içinde görünen genel bir bağımsız değişkene sahip olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-169">For example, an instantiated generic type present in the signature of a member that is visible outside its assembly shall not have a generic argument whose type is visible only within the assembly.</span></span> | <span data-ttu-id="e25a3-170">12</span><span class="sxs-lookup"><span data-stu-id="e25a3-170">12</span></span>
<span data-ttu-id="e25a3-171">Diziler</span><span class="sxs-lookup"><span data-stu-id="e25a3-171">Arrays</span></span> | [<span data-ttu-id="e25a3-172">Diziler</span><span class="sxs-lookup"><span data-stu-id="e25a3-172">Arrays</span></span>](#arrays) | <span data-ttu-id="e25a3-173">Diziler CLS uyumlu türe sahip öğelere sahip olacak ve dizinin tüm boyutları sıfır ın alt sınırlarına sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-173">Arrays shall have elements with a CLS-compliant type, and all dimensions of the array shall have lower bounds of zero.</span></span> <span data-ttu-id="e25a3-174">Yalnızca bir öğenin bir dizi olması ve dizinin öğe türüaşırı yüklemeleri ayırt etmek için gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-174">Only the fact that an item is an array and the element type of the array shall be required to distinguish between overloads.</span></span> <span data-ttu-id="e25a3-175">Aşırı yükleme iki veya daha fazla dizi türüne dayandığında eleman türleri türleri adlandırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-175">When overloading is based on two or more array types the element types shall be named types.</span></span> | <span data-ttu-id="e25a3-176">16</span><span class="sxs-lookup"><span data-stu-id="e25a3-176">16</span></span>
<span data-ttu-id="e25a3-177">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-177">Attributes</span></span> | [<span data-ttu-id="e25a3-178">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-178">Attributes</span></span>](#attributes) | <span data-ttu-id="e25a3-179">Öznitelikler, [System.Attribute](xref:System.Attribute)türünden veya ondan devralan bir türden olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-179">Attributes shall be of type [System.Attribute](xref:System.Attribute), or a type inheriting from it.</span></span> | <span data-ttu-id="e25a3-180">41</span><span class="sxs-lookup"><span data-stu-id="e25a3-180">41</span></span>
<span data-ttu-id="e25a3-181">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-181">Attributes</span></span> | [<span data-ttu-id="e25a3-182">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-182">Attributes</span></span>](#attributes) | <span data-ttu-id="e25a3-183">CLS yalnızca özel özniteliklerin kodlamalarının bir alt kümesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-183">The CLS only allows a subset of the encodings of custom attributes.</span></span> <span data-ttu-id="e25a3-184">Bu kodlamalar görünecek tek türleri (Bölüm IV bakınız): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), ve cls uyumlu baz tamsayı türüne dayalı herhangi bir numaralandırma türü.</span><span class="sxs-lookup"><span data-stu-id="e25a3-184">The only types that shall appear in these encodings are (see Partition IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), and any enumeration type based on a CLS-compliant base integer type.</span></span> | <span data-ttu-id="e25a3-185">34</span><span class="sxs-lookup"><span data-stu-id="e25a3-185">34</span></span>
<span data-ttu-id="e25a3-186">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-186">Attributes</span></span> | [<span data-ttu-id="e25a3-187">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-187">Attributes</span></span>](#attributes) | <span data-ttu-id="e25a3-188">CLS, genel olarak görünür olarak görülebilen gerekli değiştiricilere izin vermez (,`modreq`Bkz. Bölüm II), ancak isteğe bağlı değiştiricilere izin verir (`modopt`, Bölüm II'ye bakınız) anlamaz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-188">The CLS does not allow publicly visible required modifiers (`modreq`, see Partition II), but does allow optional modifiers (`modopt`, see Partition II) it does not understand.</span></span> | <span data-ttu-id="e25a3-189">35</span><span class="sxs-lookup"><span data-stu-id="e25a3-189">35</span></span>
<span data-ttu-id="e25a3-190">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="e25a3-190">Constructors</span></span> | [<span data-ttu-id="e25a3-191">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="e25a3-191">Constructors</span></span>](#constructors) | <span data-ttu-id="e25a3-192">Bir nesne oluşturucu, devralınan örnek verilerine herhangi bir erişim oluşmadan önce taban sınıfının bazı örnek oluşturucularını çağırır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-192">An object constructor shall call some instance constructor of its base class before any access occurs to inherited instance data.</span></span> <span data-ttu-id="e25a3-193">(Bu, oluşturucuları olmayan değer türleri için geçerli değildir.)</span><span class="sxs-lookup"><span data-stu-id="e25a3-193">(This does not apply to value types, which need not have constructors.)</span></span>  | <span data-ttu-id="e25a3-194">21</span><span class="sxs-lookup"><span data-stu-id="e25a3-194">21</span></span>
<span data-ttu-id="e25a3-195">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="e25a3-195">Constructors</span></span> | [<span data-ttu-id="e25a3-196">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="e25a3-196">Constructors</span></span>](#constructors) | <span data-ttu-id="e25a3-197">Bir nesne oluşturucu, bir nesnenin oluşturulmasının bir parçası dışında çağrılmayacaktır ve bir nesne iki kez başharfe batılamaz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-197">An object constructor shall not be called except as part of the creation of an object, and an object shall not be initialized twice.</span></span> | <span data-ttu-id="e25a3-198">22</span><span class="sxs-lookup"><span data-stu-id="e25a3-198">22</span></span>
<span data-ttu-id="e25a3-199">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="e25a3-199">Enumerations</span></span> | [<span data-ttu-id="e25a3-200">Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="e25a3-200">Enumerations</span></span>](#enumerations) | <span data-ttu-id="e25a3-201">Bir enum un altında yatan türü dahili CLS tamsayı türü olacak, alanın adı "value__" olacak `RTSpecialName`ve bu alan işaretlenecektir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-201">The underlying type of an enum shall be a built-in CLS integer type, the name of the field shall be "value__", and that field shall be marked `RTSpecialName`.</span></span> |  <span data-ttu-id="e25a3-202">7</span><span class="sxs-lookup"><span data-stu-id="e25a3-202">7</span></span>
<span data-ttu-id="e25a3-203">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="e25a3-203">Enumerations</span></span> | [<span data-ttu-id="e25a3-204">Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="e25a3-204">Enumerations</span></span>](#enumerations) | <span data-ttu-id="e25a3-205">[System.FlagsAttribute](xref:System.FlagsAttribute) (Bkz. Bölüm IV Kitaplığı) özel özniteliğinin varlığı veya yokluğuyla gösterilen iki farklı enum türü vardır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-205">There are two distinct kinds of enums, indicated by the presence or absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) (see Partition IV Library) custom attribute.</span></span> <span data-ttu-id="e25a3-206">Biri adlandırılmış veyasededeğerleri temsil eder; diğeri, adsız bir değer oluşturmak için biraraya getirilebilen adlandırılmış bit bayraklarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e25a3-206">One represents named integer values; the other represents named bit flags that can be combined to generate an unnamed value.</span></span> <span data-ttu-id="e25a3-207">A `enum` değeri belirtilen değerlerle sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-207">The value of an `enum` is not limited to the specified values.</span></span> |  <span data-ttu-id="e25a3-208">8</span><span class="sxs-lookup"><span data-stu-id="e25a3-208">8</span></span>
<span data-ttu-id="e25a3-209">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="e25a3-209">Enumerations</span></span> | [<span data-ttu-id="e25a3-210">Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="e25a3-210">Enumerations</span></span>](#enumerations) | <span data-ttu-id="e25a3-211">Bir enumun gerçek statik alanları, enumun kendi türüne sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-211">Literal static fields of an enum shall have the type of the enum itself.</span></span> |  <span data-ttu-id="e25a3-212">9</span><span class="sxs-lookup"><span data-stu-id="e25a3-212">9</span></span>
<span data-ttu-id="e25a3-213">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e25a3-213">Events</span></span> | [<span data-ttu-id="e25a3-214">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e25a3-214">Events</span></span>](#events) | <span data-ttu-id="e25a3-215">Bir olayı uygulayan yöntemler meta `SpecialName` verilerde işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-215">The methods that implement an event shall be marked `SpecialName` in the metadata.</span></span> |<span data-ttu-id="e25a3-216">29</span><span class="sxs-lookup"><span data-stu-id="e25a3-216">29</span></span>
<span data-ttu-id="e25a3-217">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e25a3-217">Events</span></span> | [<span data-ttu-id="e25a3-218">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e25a3-218">Events</span></span>](#events) | <span data-ttu-id="e25a3-219">Bir olayın ve onun erişenegelenlerinin erişilebilirliği aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-219">The accessibility of an event and of its accessors shall be identical.</span></span> |<span data-ttu-id="e25a3-220">30</span><span class="sxs-lookup"><span data-stu-id="e25a3-220">30</span></span>
<span data-ttu-id="e25a3-221">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e25a3-221">Events</span></span> | [<span data-ttu-id="e25a3-222">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e25a3-222">Events</span></span>](#events) | <span data-ttu-id="e25a3-223">Bir `add` `remove` olayın yöntemleri ve yöntemleri hem mevcut hem de yok olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-223">The `add` and `remove` methods for an event shall both either be present or absent.</span></span> |<span data-ttu-id="e25a3-224">31</span><span class="sxs-lookup"><span data-stu-id="e25a3-224">31</span></span>
<span data-ttu-id="e25a3-225">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e25a3-225">Events</span></span> | [<span data-ttu-id="e25a3-226">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e25a3-226">Events</span></span>](#events) | <span data-ttu-id="e25a3-227">Bir `add` `remove` olayın ve yöntemlerin her biri, etkinliğin türünü tanımlayan ve [System.Delegate'den](xref:System.Delegate)türetilecek bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-227">The `add` and `remove` methods for an event shall each take one parameter whose type defines the type of the event and that shall be derived from [System.Delegate](xref:System.Delegate).</span></span> |<span data-ttu-id="e25a3-228">32</span><span class="sxs-lookup"><span data-stu-id="e25a3-228">32</span></span>
<span data-ttu-id="e25a3-229">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e25a3-229">Events</span></span> | [<span data-ttu-id="e25a3-230">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e25a3-230">Events</span></span>](#events) | <span data-ttu-id="e25a3-231">Olaylar belirli bir adlandırma desenine uygun olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-231">Events shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="e25a3-232">CLS kural 29'da belirtilen SpecialName özniteliği, uygun ad karşılaştırmalarında yoksayılır ve tanımlayıcı kurallarına uyar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-232">The SpecialName attribute referred to in CLS rule 29 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span>  |<span data-ttu-id="e25a3-233">33</span><span class="sxs-lookup"><span data-stu-id="e25a3-233">33</span></span>
<span data-ttu-id="e25a3-234">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="e25a3-234">Exceptions</span></span> | [<span data-ttu-id="e25a3-235">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="e25a3-235">Exceptions</span></span>](#exceptions) | <span data-ttu-id="e25a3-236">Atılan nesneler [System.Exception](xref:System.Exception) türünden veya ondan devralan bir türden olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-236">Objects that are thrown shall be of type [System.Exception](xref:System.Exception) or a type inheriting from it.</span></span> <span data-ttu-id="e25a3-237">Bununla birlikte, CLS uyumlu yöntemler, diğer özel durum türlerinin yayılmasını engellemek için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-237">Nonetheless, CLS-compliant methods are not required to block the propagation of other types of exceptions.</span></span> | <span data-ttu-id="e25a3-238">40</span><span class="sxs-lookup"><span data-stu-id="e25a3-238">40</span></span>
<span data-ttu-id="e25a3-239">Genel</span><span class="sxs-lookup"><span data-stu-id="e25a3-239">General</span></span> | [<span data-ttu-id="e25a3-240">CLS uyumluluk kuralları</span><span class="sxs-lookup"><span data-stu-id="e25a3-240">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="e25a3-241">CLS kuralları yalnızca tanımlayıcı derlemenin dışında erişilebilen veya görülebilen bir türdeki parçalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-241">CLS rules apply only to those parts of a type that are accessible or visible outside of the defining assembly.</span></span> | <span data-ttu-id="e25a3-242">1</span><span class="sxs-lookup"><span data-stu-id="e25a3-242">1</span></span>
<span data-ttu-id="e25a3-243">Genel</span><span class="sxs-lookup"><span data-stu-id="e25a3-243">General</span></span> | [<span data-ttu-id="e25a3-244">CLS uyumluluk kuralları</span><span class="sxs-lookup"><span data-stu-id="e25a3-244">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="e25a3-245">CLS uyumlu olmayan türlerin üyeleri CLS uyumlu olarak işaretlenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="e25a3-245">Members of non-CLS compliant types shall not be marked CLS-compliant.</span></span> | <span data-ttu-id="e25a3-246">2</span><span class="sxs-lookup"><span data-stu-id="e25a3-246">2</span></span>
<span data-ttu-id="e25a3-247">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="e25a3-247">Generics</span></span> | [<span data-ttu-id="e25a3-248">Genel türler ve üyeler</span><span class="sxs-lookup"><span data-stu-id="e25a3-248">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="e25a3-249">İç içe geçmiş türler, en az çevreleyen tür kadar sayıda genel parametreye sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-249">Nested types shall have at least as many generic parameters as the enclosing type.</span></span> <span data-ttu-id="e25a3-250">İç içe bir türdeki genel parametreler, kendi çevreleyen türündeki genel parametrelere göre konuma göre karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-250">Generic parameters in a nested type correspond by position to the generic parameters in its enclosing type.</span></span>  | <span data-ttu-id="e25a3-251">42</span><span class="sxs-lookup"><span data-stu-id="e25a3-251">42</span></span>
<span data-ttu-id="e25a3-252">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="e25a3-252">Generics</span></span> | [<span data-ttu-id="e25a3-253">Genel türler ve üyeler</span><span class="sxs-lookup"><span data-stu-id="e25a3-253">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="e25a3-254">Genel bir türün adı, iç içe geçmemiş türde beyan edilen veya iç içe geçen türe yeni getirilen tür parametrelerinin sayısını yukarıda açıklanan kurallara göre kodlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-254">The name of a generic type shall encode the number of type parameters declared on the non-nested type, or newly introduced to the type if nested, according to the rules defined above.</span></span> | <span data-ttu-id="e25a3-255">43</span><span class="sxs-lookup"><span data-stu-id="e25a3-255">43</span></span>
<span data-ttu-id="e25a3-256">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="e25a3-256">Generics</span></span> | [<span data-ttu-id="e25a3-257">Genel türler ve üyeler</span><span class="sxs-lookup"><span data-stu-id="e25a3-257">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="e25a3-258">Genel bir tür, temel türdeki kısıtlamaların veya arabirimlerin genel tür kısıtlamaları tarafından karşılanacağını garanti etmek için yeterli kısıtlamaları yeniden beyan eder.</span><span class="sxs-lookup"><span data-stu-id="e25a3-258">A generic type shall redeclare sufficient constraints to guarantee that any constraints on the base type, or interfaces would be satisfied by the generic type constraints.</span></span> | <span data-ttu-id="e25a3-259">44</span><span class="sxs-lookup"><span data-stu-id="e25a3-259">44</span></span>
<span data-ttu-id="e25a3-260">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="e25a3-260">Generics</span></span> | [<span data-ttu-id="e25a3-261">Genel türler ve üyeler</span><span class="sxs-lookup"><span data-stu-id="e25a3-261">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="e25a3-262">Genel parametrelerde kısıtlama olarak kullanılan türler CLS uyumlu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-262">Types used as constraints on generic parameters shall themselves be CLS-compliant.</span></span> | <span data-ttu-id="e25a3-263">45</span><span class="sxs-lookup"><span data-stu-id="e25a3-263">45</span></span>
<span data-ttu-id="e25a3-264">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="e25a3-264">Generics</span></span> | [<span data-ttu-id="e25a3-265">Genel türler ve üyeler</span><span class="sxs-lookup"><span data-stu-id="e25a3-265">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="e25a3-266">Üyelerin (iç içe gelişmiş türler dahil) anlık genel bir türdeki görünürlüğü ve erişilebilirliği, genel tür bildiriminin bir bütün olarak yerine belirli anlık olarak kapsamı olarak kabul edilecektir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-266">The visibility and accessibility of members (including nested types) in an instantiated generic type shall be considered to be scoped to the specific instantiation rather than the generic type declaration as a whole.</span></span> <span data-ttu-id="e25a3-267">Bunu varsayarsak, CLS kural 12'nin görünürlük ve erişilebilirlik kuralları hala geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-267">Assuming this, the visibility and accessibility rules of CLS rule 12 still apply.</span></span> | <span data-ttu-id="e25a3-268">46</span><span class="sxs-lookup"><span data-stu-id="e25a3-268">46</span></span>
<span data-ttu-id="e25a3-269">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="e25a3-269">Generics</span></span> | [<span data-ttu-id="e25a3-270">Genel türler ve üyeler</span><span class="sxs-lookup"><span data-stu-id="e25a3-270">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="e25a3-271">Her soyut veya sanal genel yöntem için varsayılan bir somut (soyut olmayan) uygulama</span><span class="sxs-lookup"><span data-stu-id="e25a3-271">For each abstract or virtual generic method, there shall be a default concrete (nonabstract) implementation</span></span> | <span data-ttu-id="e25a3-272">47</span><span class="sxs-lookup"><span data-stu-id="e25a3-272">47</span></span>
<span data-ttu-id="e25a3-273">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="e25a3-273">Interfaces</span></span> | [<span data-ttu-id="e25a3-274">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="e25a3-274">Interfaces</span></span>](#interfaces) | <span data-ttu-id="e25a3-275">CLS uyumlu arabirimler, bunları uygulamak için CLS uyumlu olmayan yöntemlerin tanımlanmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="e25a3-275">CLS-compliant interfaces shall not require the definition of non-CLS compliant methods in order to implement them.</span></span> | <span data-ttu-id="e25a3-276">18</span><span class="sxs-lookup"><span data-stu-id="e25a3-276">18</span></span>
<span data-ttu-id="e25a3-277">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="e25a3-277">Interfaces</span></span> | [<span data-ttu-id="e25a3-278">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="e25a3-278">Interfaces</span></span>](#interfaces) | <span data-ttu-id="e25a3-279">CLS uyumlu arabirimler statik yöntemleri tanımlamaz ve alanları tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-279">CLS-compliant interfaces shall not define static methods, nor shall they define fields.</span></span> | <span data-ttu-id="e25a3-280">19</span><span class="sxs-lookup"><span data-stu-id="e25a3-280">19</span></span>
<span data-ttu-id="e25a3-281">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e25a3-281">Members</span></span> | [<span data-ttu-id="e25a3-282">Genel olarak tip üyeleri</span><span class="sxs-lookup"><span data-stu-id="e25a3-282">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="e25a3-283">Genel statik alanlar ve yöntemler CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-283">Global static fields and methods are not CLS-compliant.</span></span> | <span data-ttu-id="e25a3-284">36</span><span class="sxs-lookup"><span data-stu-id="e25a3-284">36</span></span>
<span data-ttu-id="e25a3-285">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e25a3-285">Members</span></span> | -- | <span data-ttu-id="e25a3-286">Bir literal statik değeri alan başlatma meta verilerinin kullanımı ile belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-286">The value of a literal static is specified through the use of field initialization metadata.</span></span> <span data-ttu-id="e25a3-287">CLS uyumlu bir literal, alan başlatma meta verilerinde tam olarak literal (veya temel türde, eğer bu gerçek `enum`bir gerçek se) ile aynı türde belirtilen bir değere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-287">A CLS-compliant literal must have a value specified in field initialization metadata that is of exactly the same type as the literal (or of the underlying type, if that literal is an `enum`).</span></span> | <span data-ttu-id="e25a3-288">13</span><span class="sxs-lookup"><span data-stu-id="e25a3-288">13</span></span>
<span data-ttu-id="e25a3-289">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e25a3-289">Members</span></span> | [<span data-ttu-id="e25a3-290">Genel olarak tip üyeleri</span><span class="sxs-lookup"><span data-stu-id="e25a3-290">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="e25a3-291">Vararg kısıtlaması CLS'nin bir parçası değildir ve CLS tarafından desteklenen tek çağrı sözleşmesi standart yönetilen arama kuralıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-291">The vararg constraint is not part of the CLS, and the only calling convention supported by the CLS is the standard managed calling convention.</span></span> | <span data-ttu-id="e25a3-292">15</span><span class="sxs-lookup"><span data-stu-id="e25a3-292">15</span></span>
<span data-ttu-id="e25a3-293">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="e25a3-293">Naming conventions</span></span> | [<span data-ttu-id="e25a3-294">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="e25a3-294">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="e25a3-295">Derlemeler, Unicode Standard3.0'ın Teknik Raporu'nun 15'inci ekini izleyerek, [Unicode Normalizasyon Formlarında](https://www.unicode.org/unicode/reports/tr15/tr15-18.html)çevrimiçi olarak bulunan tanımlayıcılara başlamasına ve dahil edilmesine izin verilen karakter kümesini yönetecektir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-295">Assemblies shall follow Annex 7 of Technical Report 15 of the Unicode Standard3.0 governing the set of characters permitted to start and be included in identifiers, available online at [Unicode Normalization Forms](https://www.unicode.org/unicode/reports/tr15/tr15-18.html).</span></span> <span data-ttu-id="e25a3-296">Tanımlayıcılar, Unicode Normalizasyon Formu C ile tanımlanan kanonik formatta olacaktır. CLS amaçları için, küçük harf eşlemeleri (Unicode yerel duyarsız, bire bir küçük harf eşlemeleri tarafından belirtildiği gibi) aynıysa iki tanımlayıcı aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-296">Identifiers shall be in the canonical format defined by Unicode Normalization Form C. For CLS purposes, two identifiers are the same if their lowercase mappings (as specified by the Unicode locale-insensitive, one-to-one lowercase mappings) are the same.</span></span> <span data-ttu-id="e25a3-297">Diğer bir deyişle, iki tanımlayıcının CLS altında farklı kabul edilmesi için, sadece kendi durumunda daha farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-297">That is, for two identifiers to be considered different under the CLS they shall differ in more than simply their case.</span></span> <span data-ttu-id="e25a3-298">Ancak, devralınan bir tanımı geçersiz kılmak için CLI, özgün bildirimin kesin kodlamasının kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-298">However, in order to override an inherited definition the CLI requires the precise encoding of the original declaration be used.</span></span> | <span data-ttu-id="e25a3-299">4</span><span class="sxs-lookup"><span data-stu-id="e25a3-299">4</span></span>
<span data-ttu-id="e25a3-300">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="e25a3-300">Overloading</span></span> | [<span data-ttu-id="e25a3-301">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="e25a3-301">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="e25a3-302">CLS uyumlu bir kapsamda tanıtılan tüm adlar, adların aynı olduğu ve aşırı yükleme yoluyla çözüldüğü durumlar dışında farklı türde bağımsız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-302">All names introduced in a CLS-compliant scope shall be distinct independent of kind, except where the names are identical and resolved via overloading.</span></span> <span data-ttu-id="e25a3-303">Diğer bir zamanda, CTS tek bir türün bir yöntem ve alan için aynı adı kullanmasına izin verirken, CLS bunu yapmaz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-303">That is, while the CTS allows a single type to use the same name for a method and a field, the CLS does not.</span></span> | <span data-ttu-id="e25a3-304">5</span><span class="sxs-lookup"><span data-stu-id="e25a3-304">5</span></span>
<span data-ttu-id="e25a3-305">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="e25a3-305">Overloading</span></span> | [<span data-ttu-id="e25a3-306">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="e25a3-306">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="e25a3-307">CtS farklı imzaların ayırt edilmesine izin vermesine rağmen, alanlar ve iç içe doğru türler yalnızca tanımlayıcı karşılaştırmasına göre ayrı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-307">Fields and nested types shall be distinct by identifier comparison alone, even though the CTS allows distinct signatures to be distinguished.</span></span> <span data-ttu-id="e25a3-308">Aynı ada sahip yöntemler, özellikler ve olaylar (tanımlayıcı karşılaştırmasına göre) CLS Kural 39'da belirtilenler dışında, dönüş türünden daha fazlasına göre farklılık gösterir</span><span class="sxs-lookup"><span data-stu-id="e25a3-308">Methods, properties, and events that have the same name (by identifier comparison) shall differ by more than just the return type,except as specified in CLS Rule 39</span></span> | <span data-ttu-id="e25a3-309">6</span><span class="sxs-lookup"><span data-stu-id="e25a3-309">6</span></span>
<span data-ttu-id="e25a3-310">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="e25a3-310">Overloading</span></span> | [<span data-ttu-id="e25a3-311">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="e25a3-311">Overloads</span></span>](#overloads) | <span data-ttu-id="e25a3-312">Yalnızca özellikler ve yöntemler aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-312">Only properties and methods can be overloaded.</span></span> | <span data-ttu-id="e25a3-313">37</span><span class="sxs-lookup"><span data-stu-id="e25a3-313">37</span></span>
<span data-ttu-id="e25a3-314">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="e25a3-314">Overloading</span></span> | [<span data-ttu-id="e25a3-315">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="e25a3-315">Overloads</span></span>](#overloads) |<span data-ttu-id="e25a3-316">Özellikler ve yöntemler, yalnızca parametrelerinin sayısına ve türlerine göre, `op_Implicit` `op_Explicit`adlandırılmış dönüştürme işleçleri dışında ve dönüş türlerine göre aşırı yüklenebilecek aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-316">Properties and methods can be overloaded based only on the number and types of their parameters, except the conversion operators named `op_Implicit` and `op_Explicit`, which can also be overloaded based on their return type.</span></span> | <span data-ttu-id="e25a3-317">38</span><span class="sxs-lookup"><span data-stu-id="e25a3-317">38</span></span>
<span data-ttu-id="e25a3-318">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="e25a3-318">Overloading</span></span> | -- | <span data-ttu-id="e25a3-319">Bir türde bildirilen iki veya daha fazla CLS uyumlu yöntem aynı ada sahipse ve belirli bir tür anlık yineleme kümesi için aynı parametre ve dönüş türlerine sahipse, tüm bu yöntemler bu tür anlık belirlemelerde anlamsal olarak eşdeğer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-319">If two or more CLS-compliant methods declared in a type have the same name and, for a specific set of type instantiations, they have the same parameter and return types, then all these methods shall be semantically equivalent at those type instantiations.</span></span> | <span data-ttu-id="e25a3-320">48</span><span class="sxs-lookup"><span data-stu-id="e25a3-320">48</span></span>
<span data-ttu-id="e25a3-321">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-321">Properties</span></span> | [<span data-ttu-id="e25a3-322">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-322">Properties</span></span>](#properties) | <span data-ttu-id="e25a3-323">Bir özelliğin alıcı ve ayarlayıcı yöntemlerini uygulayan `SpecialName` yöntemler meta verilerde işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-323">The methods that implement the getter and setter methods of a property shall be marked `SpecialName` in the metadata.</span></span> | <span data-ttu-id="e25a3-324">24</span><span class="sxs-lookup"><span data-stu-id="e25a3-324">24</span></span>
<span data-ttu-id="e25a3-325">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-325">Properties</span></span> | [<span data-ttu-id="e25a3-326">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-326">Properties</span></span>](#properties) | <span data-ttu-id="e25a3-327">Bir mülkün erişime girenlerin tümü statik, tümü sanal veya örnek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-327">A property’s accessors shall all be static, all be virtual, or all be instance.</span></span> | <span data-ttu-id="e25a3-328">26</span><span class="sxs-lookup"><span data-stu-id="e25a3-328">26</span></span>
<span data-ttu-id="e25a3-329">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-329">Properties</span></span> | [<span data-ttu-id="e25a3-330">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-330">Properties</span></span>](#properties) | <span data-ttu-id="e25a3-331">Bir özelliğin türü, ayarlayıcının dönüş türü ve ayarlayıcının son bağımsız değişkeninin türü olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-331">The type of a property shall be the return type of the getter and the type of the last argument of the setter.</span></span> <span data-ttu-id="e25a3-332">Özelliğin parametrelerinin türleri, ayarlayıcının parametrelerinin türleri ve ayarlayıcının son parametresi dışında tüm parametrelerin türleri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-332">The types of the parameters of the property shall be the types of the parameters to the getter and the types of all but the final parameter of the setter.</span></span> <span data-ttu-id="e25a3-333">Bu türlerin tümü CLS uyumlu olacaktır ve yönetilmeyecektir (diğer bir şekilde referans la geçirilmeyecektir).</span><span class="sxs-lookup"><span data-stu-id="e25a3-333">All of these types shall be CLS-compliant, and shall not be managed pointers (that is, shall not be passed by reference).</span></span> | <span data-ttu-id="e25a3-334">27</span><span class="sxs-lookup"><span data-stu-id="e25a3-334">27</span></span>
<span data-ttu-id="e25a3-335">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-335">Properties</span></span> | [<span data-ttu-id="e25a3-336">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-336">Properties</span></span>](#properties) | <span data-ttu-id="e25a3-337">Özellikler belirli bir adlandırma desenine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-337">Properties shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="e25a3-338">`SpecialName` CLS kural 24'te belirtilen öznitelik, uygun ad karşılaştırmalarında yoksayılır ve tanımlayıcı kurallarına uyar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-338">The `SpecialName` attribute referred to in CLS rule 24 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span> <span data-ttu-id="e25a3-339">Bir özellik bir getter yöntemi, bir ayarlayıcı yöntemi veya her ikisi de olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-339">A property shall have a getter method, a setter method, or both.</span></span> | <span data-ttu-id="e25a3-340">28</span><span class="sxs-lookup"><span data-stu-id="e25a3-340">28</span></span>
<span data-ttu-id="e25a3-341">Tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e25a3-341">Type conversion</span></span> | [<span data-ttu-id="e25a3-342">Tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e25a3-342">Type conversion</span></span>](#type-conversion) | <span data-ttu-id="e25a3-343">op_Implicit veya op_Explicit sağlanmışsa, zorlamayı sağlamak için alternatif bir araç sağlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-343">If either op_Implicit or op_Explicit is provided, an alternate means of providing the coercion shall be provided.</span></span> | <span data-ttu-id="e25a3-344">39</span><span class="sxs-lookup"><span data-stu-id="e25a3-344">39</span></span>
<span data-ttu-id="e25a3-345">Türler</span><span class="sxs-lookup"><span data-stu-id="e25a3-345">Types</span></span> | [<span data-ttu-id="e25a3-346">Üye imzatürleri ve türleri</span><span class="sxs-lookup"><span data-stu-id="e25a3-346">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="e25a3-347">Kutulu değer türleri CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-347">Boxed value types are not CLS-compliant.</span></span> | <span data-ttu-id="e25a3-348">3</span><span class="sxs-lookup"><span data-stu-id="e25a3-348">3</span></span>
<span data-ttu-id="e25a3-349">Türler</span><span class="sxs-lookup"><span data-stu-id="e25a3-349">Types</span></span> | [<span data-ttu-id="e25a3-350">Üye imzatürleri ve türleri</span><span class="sxs-lookup"><span data-stu-id="e25a3-350">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="e25a3-351">İmzada görünen tüm türler CLS uyumlu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-351">All types appearing in a signature shall be CLS-compliant.</span></span> <span data-ttu-id="e25a3-352">Anlık genel bir tür oluşturan tüm türler CLS uyumlu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-352">All types composing an instantiated generic type shall be CLS-compliant.</span></span> | <span data-ttu-id="e25a3-353">11</span><span class="sxs-lookup"><span data-stu-id="e25a3-353">11</span></span>
<span data-ttu-id="e25a3-354">Türler</span><span class="sxs-lookup"><span data-stu-id="e25a3-354">Types</span></span> | [<span data-ttu-id="e25a3-355">Üye imzatürleri ve türleri</span><span class="sxs-lookup"><span data-stu-id="e25a3-355">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="e25a3-356">Yazılan başvurular CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-356">Typed references are not CLS-compliant.</span></span> | <span data-ttu-id="e25a3-357">14</span><span class="sxs-lookup"><span data-stu-id="e25a3-357">14</span></span>
<span data-ttu-id="e25a3-358">Türler</span><span class="sxs-lookup"><span data-stu-id="e25a3-358">Types</span></span> | [<span data-ttu-id="e25a3-359">Üye imzatürleri ve türleri</span><span class="sxs-lookup"><span data-stu-id="e25a3-359">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="e25a3-360">Yönetilmeyen işaretçi türleri CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-360">Unmanaged pointer types are not CLS-compliant.</span></span> | <span data-ttu-id="e25a3-361">17</span><span class="sxs-lookup"><span data-stu-id="e25a3-361">17</span></span>
<span data-ttu-id="e25a3-362">Türler</span><span class="sxs-lookup"><span data-stu-id="e25a3-362">Types</span></span> | [<span data-ttu-id="e25a3-363">Üye imzatürleri ve türleri</span><span class="sxs-lookup"><span data-stu-id="e25a3-363">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="e25a3-364">CLS uyumlu sınıflar, değer türleri ve arayüzler, CLS uyumlu olmayan üyelerin uygulanmasını gerektirmez</span><span class="sxs-lookup"><span data-stu-id="e25a3-364">CLS-compliant classes, value types, and interfaces shall not require the implementation of non-CLS-compliant members</span></span> | <span data-ttu-id="e25a3-365">20</span><span class="sxs-lookup"><span data-stu-id="e25a3-365">20</span></span>
<span data-ttu-id="e25a3-366">Türler</span><span class="sxs-lookup"><span data-stu-id="e25a3-366">Types</span></span> | [<span data-ttu-id="e25a3-367">Üye imzatürleri ve türleri</span><span class="sxs-lookup"><span data-stu-id="e25a3-367">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="e25a3-368">[System.Object](xref:System.Object) CLS uyumludur.</span><span class="sxs-lookup"><span data-stu-id="e25a3-368">[System.Object](xref:System.Object) is CLS-compliant.</span></span> <span data-ttu-id="e25a3-369">CLS uyumlu diğer herhangi bir sınıf, CLS uyumlu bir sınıftan devralınacaktır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-369">Any other CLS-compliant class shall inherit from a CLS-compliant class.</span></span> | <span data-ttu-id="e25a3-370">23</span><span class="sxs-lookup"><span data-stu-id="e25a3-370">23</span></span>

### <a name="types-and-type-member-signatures"></a><span data-ttu-id="e25a3-371">Üye imzatürleri ve türleri</span><span class="sxs-lookup"><span data-stu-id="e25a3-371">Types and type member signatures</span></span>

<span data-ttu-id="e25a3-372">[System.Object](xref:System.Object) türü CLS uyumludur ve .NET Framework türü sistemindeki tüm nesne türlerinin temel türüdür.</span><span class="sxs-lookup"><span data-stu-id="e25a3-372">The [System.Object](xref:System.Object) type is CLS-compliant and is the base type of all object types in the .NET Framework type system.</span></span> <span data-ttu-id="e25a3-373">.NET Framework'deki devralma ya örtülüdür (örneğin, [String](xref:System.String) sınıfı `Object` örtük olarak sınıftan devralır) veya açık (örneğin, [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) sınıfı, [Özel Durum](xref:System.Exception) sınıfından açıkça devralan Bağımsız [Durum](xref:System.ArgumentException) sınıfından açıkça devralır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-373">Inheritance in the .NET Framework is either implicit (for example, the [String](xref:System.String) class implicitly inherits from the `Object` class) or explicit (for example, the [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) class explicitly inherits from the [ArgumentException](xref:System.ArgumentException) class, which explicitly inherits from the [Exception](xref:System.Exception) class.</span></span> <span data-ttu-id="e25a3-374">Türetilen bir türün CLS uyumlu olabilmesi için, taban türü de CLS uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-374">For a derived type to be CLS compliant, its base type must also be CLS-compliant.</span></span>

<span data-ttu-id="e25a3-375">Aşağıdaki örnekte, taban türü CLS uyumlu olmayan türetilmiş bir tür gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-375">The following example shows a derived type whose base type is not CLS-compliant.</span></span> <span data-ttu-id="e25a3-376">İmzasız 32 `Counter` bit tamsayı kullanan bir taban sınıfı sayaç olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-376">It defines a base `Counter` class that uses an unsigned 32-bit integer as a counter.</span></span> <span data-ttu-id="e25a3-377">Sınıf imzasız bir karşıcıyı sararak sayaç işlevselliği sağladığından, sınıf CLS uyumlu olmayan olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-377">Because the class provides counter functionality by wrapping an unsigned integer, the class is marked as non-CLS-compliant.</span></span> <span data-ttu-id="e25a3-378">Sonuç olarak, türetilmiş `NonZeroCounter`bir sınıf, CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-378">As a result, a derived class, `NonZeroCounter`, is also not CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

[CLSCompliant(false)]
public class Counter
{
   UInt32 ctr;

   public Counter()
   {
      ctr = 0;
   }

   protected Counter(UInt32 ctr)
   {
      this.ctr = ctr;
   }

   public override string ToString()
   {
      return $"{ctr}). ";
   }

   public UInt32 Value
   {
      get { return ctr; }
   }

   public void Increment()
   {
      ctr += (uint) 1;
   }
}

public class NonZeroCounter : Counter
{
   public NonZeroCounter(int startIndex) : this((uint) startIndex)
   {
   }

   private NonZeroCounter(UInt32 startIndex) : base(startIndex)
   {
   }
}
// Compilation produces a compiler warning like the following:
//    Type3.cs(37,14): warning CS3009: 'NonZeroCounter': base type 'Counter' is not
//            CLS-compliant
//    Type3.cs(7,14): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>

<CLSCompliant(False)> _
Public Class Counter
   Dim ctr As UInt32

   Public Sub New
      ctr = 0
   End Sub

   Protected Sub New(ctr As UInt32)
      ctr = ctr
   End Sub

   Public Overrides Function ToString() As String
      Return $"{ctr}). "
   End Function

   Public ReadOnly Property Value As UInt32
      Get
         Return ctr
      End Get
   End Property

   Public Sub Increment()
      ctr += CType(1, UInt32)
   End Sub
End Class

Public Class NonZeroCounter : Inherits Counter
   Public Sub New(startIndex As Integer)
      MyClass.New(CType(startIndex, UInt32))
   End Sub

   Private Sub New(startIndex As UInt32)
      MyBase.New(CType(startIndex, UInt32))
   End Sub
End Class
' Compilation produces a compiler warning like the following:
'    Type3.vb(34) : warning BC40026: 'NonZeroCounter' is not CLS-compliant
'    because it derives from 'Counter', which is not CLS-compliant.
'
'    Public Class NonZeroCounter : Inherits Counter
'                 ~~~~~~~~~~~~~~
```

<span data-ttu-id="e25a3-379">Bir yöntemin dönüş türü veya özellik türü de dahil olmak üzere üye imzalarda görünen tüm türler CLS uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-379">All types that appear in member signatures, including a method's return type or a property type, must be CLS-compliant.</span></span> <span data-ttu-id="e25a3-380">Buna ek olarak, genel türleri için:</span><span class="sxs-lookup"><span data-stu-id="e25a3-380">In addition, for generic types:</span></span>

* <span data-ttu-id="e25a3-381">Anında genel bir tür oluşturan tüm türler CLS uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-381">All types that compose an instantiated generic type must be CLS-compliant.</span></span>

* <span data-ttu-id="e25a3-382">Genel parametrelerde kısıtlama olarak kullanılan tüm türler CLS uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-382">All types used as constraints on generic parameters must be CLS-compliant.</span></span>

<span data-ttu-id="e25a3-383">.NET [ortak tür sistemi,](common-type-system.md) ortak dil çalışma zamanı tarafından doğrudan desteklenen ve bir derlemenin meta verilerinde özel olarak kodlanan bir dizi yerleşik türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-383">The .NET [common type system](common-type-system.md) includes a number of built-in types that are supported directly by the common language runtime and are specially encoded in an assembly's metadata.</span></span> <span data-ttu-id="e25a3-384">Bu içsel türlerden, aşağıdaki tabloda listelenen türleri CLS uyumludur.</span><span class="sxs-lookup"><span data-stu-id="e25a3-384">Of these intrinsic types, the types listed in the following table are CLS-compliant.</span></span>

<span data-ttu-id="e25a3-385">CLS uyumlu tip</span><span class="sxs-lookup"><span data-stu-id="e25a3-385">CLS-compliant type</span></span> | <span data-ttu-id="e25a3-386">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e25a3-386">Description</span></span>
------------------ | -----------
[<span data-ttu-id="e25a3-387">Bayt</span><span class="sxs-lookup"><span data-stu-id="e25a3-387">Byte</span></span>](xref:System.Byte) | <span data-ttu-id="e25a3-388">8 bit imzasız tümseci</span><span class="sxs-lookup"><span data-stu-id="e25a3-388">8-bit unsigned integer</span></span>
[<span data-ttu-id="e25a3-389">Int16</span><span class="sxs-lookup"><span data-stu-id="e25a3-389">Int16</span></span>](xref:System.Int16) | <span data-ttu-id="e25a3-390">16 bit imzalı tümseci</span><span class="sxs-lookup"><span data-stu-id="e25a3-390">16-bit signed integer</span></span>
[<span data-ttu-id="e25a3-391">Int32</span><span class="sxs-lookup"><span data-stu-id="e25a3-391">Int32</span></span>](xref:System.Int32) | <span data-ttu-id="e25a3-392">32 bit imzalı tümseci</span><span class="sxs-lookup"><span data-stu-id="e25a3-392">32-bit signed integer</span></span>
[<span data-ttu-id="e25a3-393">Int64</span><span class="sxs-lookup"><span data-stu-id="e25a3-393">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="e25a3-394">64 bit imzalı tümseci</span><span class="sxs-lookup"><span data-stu-id="e25a3-394">64-bit signed integer</span></span>
[<span data-ttu-id="e25a3-395">Tek</span><span class="sxs-lookup"><span data-stu-id="e25a3-395">Single</span></span>](xref:System.Single) | <span data-ttu-id="e25a3-396">Tek hassas kayan nokta değeri</span><span class="sxs-lookup"><span data-stu-id="e25a3-396">Single-precision floating-point value</span></span>
[<span data-ttu-id="e25a3-397">Çift</span><span class="sxs-lookup"><span data-stu-id="e25a3-397">Double</span></span>](xref:System.Double) | <span data-ttu-id="e25a3-398">Çift duyarlıklı kayan nokta değeri</span><span class="sxs-lookup"><span data-stu-id="e25a3-398">Double-precision floating-point value</span></span>
[<span data-ttu-id="e25a3-399">Boole</span><span class="sxs-lookup"><span data-stu-id="e25a3-399">Boolean</span></span>](xref:System.Boolean) | <span data-ttu-id="e25a3-400">doğru veya yanlış değer türü</span><span class="sxs-lookup"><span data-stu-id="e25a3-400">true or false value type</span></span>
[<span data-ttu-id="e25a3-401">Char</span><span class="sxs-lookup"><span data-stu-id="e25a3-401">Char</span></span>](xref:System.Char) | <span data-ttu-id="e25a3-402">UTF-16 kodlanmış kod birimi</span><span class="sxs-lookup"><span data-stu-id="e25a3-402">UTF-16 encoded code unit</span></span>
[<span data-ttu-id="e25a3-403">On -da -lık</span><span class="sxs-lookup"><span data-stu-id="e25a3-403">Decimal</span></span>](xref:System.Decimal) | <span data-ttu-id="e25a3-404">Kayan olmayan nokta ondalık sayı</span><span class="sxs-lookup"><span data-stu-id="e25a3-404">Non-floating-point decimal number</span></span>
[<span data-ttu-id="e25a3-405">ıntptr</span><span class="sxs-lookup"><span data-stu-id="e25a3-405">IntPtr</span></span>](xref:System.IntPtr) | <span data-ttu-id="e25a3-406">Platform tanımlı bir boyutun işaretçisi veya tutamacı</span><span class="sxs-lookup"><span data-stu-id="e25a3-406">Pointer or handle of a platform-defined size</span></span>
[<span data-ttu-id="e25a3-407">Dize</span><span class="sxs-lookup"><span data-stu-id="e25a3-407">String</span></span>](xref:System.String) | <span data-ttu-id="e25a3-408">Sıfır, bir veya daha fazla Char nesnesinin toplanması</span><span class="sxs-lookup"><span data-stu-id="e25a3-408">Collection of zero, one, or more Char objects</span></span>

<span data-ttu-id="e25a3-409">Aşağıdaki tabloda listelenen içsel türleri CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-409">The intrinsic types listed in the following table are not CLS-Compliant.</span></span>

<span data-ttu-id="e25a3-410">Uyumlu olmayan tür</span><span class="sxs-lookup"><span data-stu-id="e25a3-410">Non-compliant type</span></span> | <span data-ttu-id="e25a3-411">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e25a3-411">Description</span></span> | <span data-ttu-id="e25a3-412">CLS uyumlu alternatif</span><span class="sxs-lookup"><span data-stu-id="e25a3-412">CLS-compliant alternative</span></span>
------------------ | ----------- | -------------------------
[<span data-ttu-id="e25a3-413">Sbyte</span><span class="sxs-lookup"><span data-stu-id="e25a3-413">SByte</span></span>](xref:System.SByte) | <span data-ttu-id="e25a3-414">8 bit imzalı imzalı veri türü</span><span class="sxs-lookup"><span data-stu-id="e25a3-414">8-bit signed integer data type</span></span> | [<span data-ttu-id="e25a3-415">Int16</span><span class="sxs-lookup"><span data-stu-id="e25a3-415">Int16</span></span>](xref:System.Int16)
[<span data-ttu-id="e25a3-416">UInt16</span><span class="sxs-lookup"><span data-stu-id="e25a3-416">UInt16</span></span>](xref:System.UInt16) | <span data-ttu-id="e25a3-417">16 bit imzasız tümseci</span><span class="sxs-lookup"><span data-stu-id="e25a3-417">16-bit unsigned integer</span></span> | [<span data-ttu-id="e25a3-418">Int32</span><span class="sxs-lookup"><span data-stu-id="e25a3-418">Int32</span></span>](xref:System.Int32)
[<span data-ttu-id="e25a3-419">UInt32</span><span class="sxs-lookup"><span data-stu-id="e25a3-419">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="e25a3-420">32 bit imzasız tümseci</span><span class="sxs-lookup"><span data-stu-id="e25a3-420">32-bit unsigned integer</span></span> | [<span data-ttu-id="e25a3-421">Int64</span><span class="sxs-lookup"><span data-stu-id="e25a3-421">Int64</span></span>](xref:System.Int64)
[<span data-ttu-id="e25a3-422">UInt64</span><span class="sxs-lookup"><span data-stu-id="e25a3-422">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="e25a3-423">64 bit imzasız tümseci</span><span class="sxs-lookup"><span data-stu-id="e25a3-423">64-bit unsigned integer</span></span> | <span data-ttu-id="e25a3-424">[Int64](xref:System.Int64) (taşabilir), [BigInteger](xref:System.Numerics.BigInteger)veya [Çift](xref:System.Double)</span><span class="sxs-lookup"><span data-stu-id="e25a3-424">[Int64](xref:System.Int64) (may overflow), [BigInteger](xref:System.Numerics.BigInteger), or [Double](xref:System.Double)</span></span>
[<span data-ttu-id="e25a3-425">Uıntptr</span><span class="sxs-lookup"><span data-stu-id="e25a3-425">UIntPtr</span></span>](xref:System.UIntPtr) | <span data-ttu-id="e25a3-426">İmzasız işaretçi veya tanıtıcı</span><span class="sxs-lookup"><span data-stu-id="e25a3-426">Unsigned pointer or handle</span></span> | [<span data-ttu-id="e25a3-427">ıntptr</span><span class="sxs-lookup"><span data-stu-id="e25a3-427">IntPtr</span></span>](xref:System.IntPtr)

<span data-ttu-id="e25a3-428">.NET Framework Class Kitaplığı veya başka bir sınıf kitaplığı CLS uyumlu olmayan diğer türleri içerebilir; örneğin:</span><span class="sxs-lookup"><span data-stu-id="e25a3-428">The .NET Framework Class Library or any other class library may include other types that aren't CLS-compliant; for example:</span></span>

* <span data-ttu-id="e25a3-429">Kutulu değer türleri.</span><span class="sxs-lookup"><span data-stu-id="e25a3-429">Boxed value types.</span></span> <span data-ttu-id="e25a3-430">Aşağıdaki C# örneği, \* adlı `int` `Value`türde bir ortak özelliği olan bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e25a3-430">The following C# example creates a class that has a public property of type `int`\* named `Value`.</span></span> <span data-ttu-id="e25a3-431">`int`\* kutulu bir değer türü olduğundan, derleyici onu CLS uyumlu olmayan olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="e25a3-431">Because an `int`\* is a boxed value type, the compiler flags it as non-CLS-compliant.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public unsafe class TestClass
{
   private int* val;

   public TestClass(int number)
   {
      val = (int*) number;
   }

   public int* Value {
      get { return val; }
   }
}
// The compiler generates the following output when compiling this example:
//        warning CS3003: Type of 'TestClass.Value' is not CLS-compliant
```

* <span data-ttu-id="e25a3-432">Bir nesneye ve bir türe başvuru içeren özel yapılar olan yazılı başvurular.</span><span class="sxs-lookup"><span data-stu-id="e25a3-432">Typed references, which are special constructs that contain a reference to an object and a reference to a type.</span></span>

<span data-ttu-id="e25a3-433">Bir tür CLS uyumlu değilse, [CLSCompliant Attribute özniteliğini](xref:System.CLSCompliantAttribute) bir değeri `false` olan bir *isCompliant* parametresi ile uygulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="e25a3-433">If a type is not CLS-compliant, you should apply the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute with an *isCompliant* parameter with a value of `false` to it.</span></span> <span data-ttu-id="e25a3-434">Daha fazla bilgi için [CLSCompliant Attribute öznitelik](#the-clscompliantattribute-attribute) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e25a3-434">For more information, see the [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute) section.</span></span>

<span data-ttu-id="e25a3-435">Aşağıdaki örnekte, bir yöntem imzasında ve genel tür anında cls uyumluluğu sorunu gösteriş göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-435">The following example illustrates the problem of CLS compliance in a method signature and in generic type instantiation.</span></span> <span data-ttu-id="e25a3-436">Bu türü `InvoiceItem` [UInt32](xref:System.UInt32)özelliği olan bir sınıf tanımlar, türü Nullable bir özelliği [(UInt32)](xref:System.Nullable%601)ve `UInt32` `Nullable(Of UInt32)`türü parametreleri ile bir yapıcı ve .</span><span class="sxs-lookup"><span data-stu-id="e25a3-436">It defines an `InvoiceItem` class with a property of type [UInt32](xref:System.UInt32), a property of type [Nullable(Of UInt32)](xref:System.Nullable%601), and a constructor with parameters of type `UInt32` and `Nullable(Of UInt32)`.</span></span> <span data-ttu-id="e25a3-437">Bu örneği derlemeye çalıştığınızda dört derleyici uyarısı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="e25a3-437">You get four compiler warnings when you try to compile this example.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<uint> qty;

   public InvoiceItem(uint sku, Nullable<uint> quantity)
   {
      itemId = sku;
      qty = quantity;
   }

   public Nullable<uint> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public uint InvoiceId
   {
      get { return invId; }
      set { invId = value; }
   }
}
// The attempt to compile the example displays the following output:
//    Type1.cs(13,23): warning CS3001: Argument type 'uint' is not CLS-compliant
//    Type1.cs(13,33): warning CS3001: Argument type 'uint?' is not CLS-compliant
//    Type1.cs(19,26): warning CS3003: Type of 'InvoiceItem.Quantity' is not CLS-compliant
//    Type1.cs(25,16): warning CS3003: Type of 'InvoiceItem.InvoiceId' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of UInteger)

   Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
      itemId = sku
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of UInteger)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As UInteger
      Get
         Return invId
      End Get
      Set
         invId = value
      End Set
   End Property
End Class
' The attempt to compile the example displays output similar to the following:
'    Type1.vb(13) : warning BC40028: Type of parameter 'sku' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                      ~~~
'    Type1.vb(13) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                                                               ~~~~~~~~
'    Type1.vb(18) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Property Quantity As Nullable(Of UInteger)
'                                               ~~~~~~~~
'    Type1.vb(27) : warning BC40027: Return type of function 'InvoiceId' is not CLS-compliant.
'
'       Public Property InvoiceId As UInteger
```

<span data-ttu-id="e25a3-438">Derleyici uyarılarını ortadan kaldırmak `InvoiceItem` için, genel arabirimdeki CLS uyumlu olmayan türleri uyumlu türlerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e25a3-438">To eliminate the compiler warnings, replace the non-CLS-compliant types in the `InvoiceItem` public interface with compliant types:</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<int> qty;

   public InvoiceItem(int sku, Nullable<int> quantity)
   {
      if (sku <= 0)
         throw new ArgumentOutOfRangeException("The item number is zero or negative.");
      itemId = (uint) sku;

      qty = quantity;
   }

   public Nullable<int> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public int InvoiceId
   {
      get { return (int) invId; }
      set {
         if (value <= 0)
            throw new ArgumentOutOfRangeException("The invoice number is zero or negative.");
         invId = (uint) value; }
   }
}
```

```vb
Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of Integer)

   Public Sub New(sku As Integer, quantity As Nullable(Of Integer))
      If sku <= 0 Then
         Throw New ArgumentOutOfRangeException("The item number is zero or negative.")
      End If
      itemId = CUInt(sku)
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of Integer)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As Integer
      Get
         Return CInt(invId)
      End Get
      Set
         invId = CUInt(value)
      End Set
   End Property
End Class
```

<span data-ttu-id="e25a3-439">Listelenen belirli türlere ek olarak, bazı tür kategorileri CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-439">In addition to the specific types listed, some categories of types are not CLS compliant.</span></span> <span data-ttu-id="e25a3-440">Bunlar, yönetilmeyen işaretçi türleri ve işlev işaretçisi türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-440">These include unmanaged pointer types and function pointer types.</span></span> <span data-ttu-id="e25a3-441">Aşağıdaki örnek, bir tamsayı dizisi oluşturmak için bir tamsayı işaretçisi kullandığından derleyici uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e25a3-441">The following example generates a compiler warning because it uses a pointer to an integer to create an array of integers.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

<span data-ttu-id="e25a3-442">CLS uyumlu soyut sınıflar için (diğer `abstract` bir deyişle, c#olarak işaretlenmiş sınıflar), sınıfın tüm üyeleri de CLS uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-442">For CLS-compliant abstract classes (that is, classes marked as `abstract` in C#), all members of the class must also be CLS-compliant.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="e25a3-443">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="e25a3-443">Naming conventions</span></span>

<span data-ttu-id="e25a3-444">Bazı programlama dilleri büyük/küçük harf duyarlı olduğundan, tanımlayıcılar (ad alanlarının adları, türleri ve üyeleri gibi) büyük/küçük harften daha fazla farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-444">Because some programming languages are case-insensitive, identifiers (such as the names of namespaces, types, and members) must differ by more than case.</span></span> <span data-ttu-id="e25a3-445">Küçük eşlemeleri aynıysa, iki tanımlayıcı eşdeğer olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-445">Two identifiers are considered equivalent if their lowercase mappings are the same.</span></span> <span data-ttu-id="e25a3-446">Aşağıdaki C# örneği iki ortak `Person` sınıf `person`tanımlar ve .</span><span class="sxs-lookup"><span data-stu-id="e25a3-446">The following C# example defines two public classes, `Person` and `person`.</span></span> <span data-ttu-id="e25a3-447">Yalnızca duruma göre farklılık gösterirler, C# derleyicisi bunları CLS uyumlu değil olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="e25a3-447">Because they differ only by case, the C# compiler flags them as not CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person : person
{

}

public class person
{

}
// Compilation produces a compiler warning like the following:
//    Naming1.cs(11,14): warning CS3005: Identifier 'person' differing
//                       only in case is not CLS-compliant
//    Naming1.cs(6,14): (Location of symbol related to previous warning)
```

<span data-ttu-id="e25a3-448">Ad alanları, türleri ve üyeleri gibi programlama dili tanımlayıcıları [Unicode Standart 3.0, Teknik Rapor 15, Ek 7'ye](https://www.unicode.org/reports/tr15/tr15-18.html)uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-448">Programming language identifiers, such as the names of namespaces, types, and members, must conform to the [Unicode Standard 3.0, Technical Report 15, Annex 7](https://www.unicode.org/reports/tr15/tr15-18.html).</span></span> <span data-ttu-id="e25a3-449">Bu şu anlama gelir:</span><span class="sxs-lookup"><span data-stu-id="e25a3-449">This means that:</span></span>

* <span data-ttu-id="e25a3-450">Bir tanımlayıcının ilk karakteri herhangi bir Unicode büyük harf, küçük harf, başlık büyük harf, değiştirici mektup, diğer harf veya harf numarası olabilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-450">The first character of an identifier can be any Unicode uppercase letter, lowercase letter, title case letter, modifier letter, other letter, or letter number.</span></span> <span data-ttu-id="e25a3-451">Unicode karakter kategorileri hakkında bilgi için [System.Globalization.UnicodeKategori](xref:System.Globalization.UnicodeCategory) numaralandırma'ya bakın.</span><span class="sxs-lookup"><span data-stu-id="e25a3-451">For information on Unicode character categories, see the [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) enumeration.</span></span>

* <span data-ttu-id="e25a3-452">Sonraki karakterler ilk karakter olarak kategorilerden herhangi birinden olabilir ve aralık olmayan işaretleri, işaretleri birleştirme aralığı, ondalık sayılar, bağlayıcı noktalama işaretleri ve biçimlendirme kodlarını da içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-452">Subsequent characters can be from any of the categories as the first character, and can also include non-spacing marks, spacing combining marks, decimal numbers, connector punctuations, and formatting codes.</span></span>

<span data-ttu-id="e25a3-453">Tanımlayıcıları karşılaştırmadan önce, biçimlendirme kodlarını filtrelemeniz ve tanımlayıcıları Unicode Normalization Form C'ye dönüştürmeniz gerekir, çünkü tek bir karakter birden çok UTF-16 kodlanmış kod birimi tarafından temsil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-453">Before you compare identifiers, you should filter out formatting codes and convert the identifiers to Unicode Normalization Form C, because a single character can be represented by multiple UTF-16-encoded code units.</span></span> <span data-ttu-id="e25a3-454">Unicode Normalization Form C'de aynı kod birimlerini oluşturan karakter dizileri CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-454">Character sequences that produce the same code units in Unicode Normalization Form C are not CLS-compliant.</span></span> <span data-ttu-id="e25a3-455">Aşağıdaki örnek, ANGSTROM `Å`SIGN (U+212B) karakterinden oluşan bir özellik ve `Å` LATIN BÜYÜK HARFLİ A RING YU (U+00C5) karakterinden oluşan ikinci bir özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-455">The following example defines a property named `Å`, which consists of the character ANGSTROM SIGN (U+212B), and a second property named `Å` which consists of the character LATIN CAPITAL LETTER A WITH RING ABOVE (U+00C5).</span></span> <span data-ttu-id="e25a3-456">C# derleyicisi kaynak kodunu CLS uyumlu olmayan olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="e25a3-456">The C# compiler flags the source code as non-CLS-compliant.</span></span>

```csharp
public class Size
{
   private double a1;
   private double a2;

   public double Å
   {
       get { return a1; }
       set { a1 = value; }
   }

   public double Å
   {
       get { return a2; }
       set { a2 = value; }
   }
}
// Compilation produces a compiler warning like the following:
//    Naming2a.cs(16,18): warning CS3005: Identifier 'Size.Å' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(10,18): (Location of symbol related to previous warning)
//    Naming2a.cs(18,8): warning CS3005: Identifier 'Size.Å.get' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(12,8): (Location of symbol related to previous warning)
//    Naming2a.cs(19,8): warning CS3005: Identifier 'Size.Å.set' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(13,8): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>
Public Class Size
   Private a1 As Double
   Private a2 As Double

   Public Property Å As Double
       Get
          Return a1
       End Get
       Set
          a1 = value
       End Set
   End Property

   Public Property Å As Double
       Get
          Return a2
       End Get
       Set
          a2 = value
       End Set
   End Property
End Class
' Compilation produces a compiler warning like the following:
'    Naming1.vb(9) : error BC30269: 'Public Property Å As Double' has multiple definitions
'     with identical signatures.
'
'       Public Property Å As Double
'                       ~
```

<span data-ttu-id="e25a3-457">Belirli bir kapsamdaki üye adları (derlemedeki ad alanları, ad alanı içindeki türler veya bir tür içindeki üyeler gibi) aşırı yükleme yoluyla çözülen adlar dışında benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-457">Member names within a particular scope (such as the namespaces within an assembly, the types within a namespace, or the members within a type) must be unique except for names that are resolved through overloading.</span></span> <span data-ttu-id="e25a3-458">Bu gereksinim, farklı türde üye oldukları sürece kapsam daki birden çok üyenin aynı adlara sahip olmasını sağlayan ortak tür sisteminden daha sıkıdır (örneğin, biri bir yöntem, diğeri bir alandır).</span><span class="sxs-lookup"><span data-stu-id="e25a3-458">This requirement is more stringent than that of the common type system, which allows multiple members within a scope to have identical names as long as they are different kinds of members (for example, one is a method and one is a field).</span></span> <span data-ttu-id="e25a3-459">Özellikle, tür üyeleri için:</span><span class="sxs-lookup"><span data-stu-id="e25a3-459">In particular, for type members:</span></span>

* <span data-ttu-id="e25a3-460">Alanlar ve iç içe türler tek başına adıyla ayırt edilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-460">Fields and nested types are distinguished by name alone.</span></span>

* <span data-ttu-id="e25a3-461">Aynı ada sahip yöntemler, özellikler ve olaylar, dönüş türünden daha fazla olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-461">Methods, properties, and events that have the same name must differ by more than just return type.</span></span>

<span data-ttu-id="e25a3-462">Aşağıdaki örnek, üye adların kendi kapsamları içinde benzersiz olması gereksinimini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-462">The following example illustrates the requirement that member names must be unique within their scope.</span></span> <span data-ttu-id="e25a3-463">Adı geçen dört `Converter` üyeyi içeren `Conversion`bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-463">It defines a class named `Converter` that includes four members named `Conversion`.</span></span> <span data-ttu-id="e25a3-464">Üçü yöntem, biri de bir özellik.</span><span class="sxs-lookup"><span data-stu-id="e25a3-464">Three are methods, and one is a property.</span></span> <span data-ttu-id="e25a3-465">Parametre `Int64` içeren yöntem benzersiz adlandırılmış, ancak parametreli `Int32` iki yöntem değildir, çünkü iade değeri üyenin imzasının bir parçası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="e25a3-465">The method that includes an `Int64` parameter is uniquely named, but the two methods with an `Int32` parameter are not, because return value is not considered a part of a member's signature.</span></span> <span data-ttu-id="e25a3-466">Özellikler `Conversion` aşırı yüklenen yöntemlerle aynı ada sahip olamayacağından, özellik de bu gereksinimi ihlal eder.</span><span class="sxs-lookup"><span data-stu-id="e25a3-466">The `Conversion` property also violates this requirement, because properties cannot have the same name as overloaded methods.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Converter
{
   public double Conversion(int number)
   {
      return (double) number;
   }

   public float Conversion(int number)
   {
      return (float) number;
   }

   public double Conversion(long number)
   {
      return (double) number;
   }

   public bool Conversion
   {
      get { return true; }
   }
}
// Compilation produces a compiler error like the following:
//    Naming3.cs(13,17): error CS0111: Type 'Converter' already defines a member called
//            'Conversion' with the same parameter types
//    Naming3.cs(8,18): (Location of symbol related to previous error)
//    Naming3.cs(23,16): error CS0102: The type 'Converter' already contains a definition for
//            'Conversion'
//    Naming3.cs(8,18): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Converter
   Public Function Conversion(number As Integer) As Double
      Return CDbl(number)
   End Function

   Public Function Conversion(number As Integer) As Single
      Return CSng(number)
   End Function

   Public Function Conversion(number As Long) As Double
      Return CDbl(number)
   End Function

   Public ReadOnly Property Conversion As Boolean
      Get
         Return True
      End Get
   End Property
End Class
' Compilation produces a compiler error like the following:
'    Naming3.vb(8) : error BC30301: 'Public Function Conversion(number As Integer) As Double'
'                    and 'Public Function Conversion(number As Integer) As Single' cannot
'                    overload each other because they differ only by return types.
'
'       Public Function Conversion(number As Integer) As Double
'                       ~~~~~~~~~~
'    Naming3.vb(20) : error BC30260: 'Conversion' is already declared as 'Public Function
'                     Conversion(number As Integer) As Single' in this class.
'
'       Public ReadOnly Property Conversion As Boolean
'                                ~~~~~~~~~~
```

<span data-ttu-id="e25a3-467">Tek tek diller benzersiz anahtar kelimeler içerir, bu nedenle ortak dil çalışma zamanını hedefleyen diller, anahtar kelimelerle çakışan tanımlayıcılara (tür adları gibi) başvurmak için bazı mekanizmalar da sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-467">Individual languages include unique keywords, so languages that target the common language runtime must also provide some mechanism for referencing identifiers (such as type names) that coincide with keywords.</span></span> <span data-ttu-id="e25a3-468">Örneğin, `case` hem C# hem de Visual Basic'te kullanılan bir anahtar kelimedir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-468">For example, `case` is a keyword in both C# and Visual Basic.</span></span> <span data-ttu-id="e25a3-469">Ancak, aşağıdaki Visual Basic örneği, açılış ve kapanış `case` ayraçlarını kullanarak `case` anahtar kelimeden adlı bir sınıfı ayrıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-469">However, the following Visual Basic example is able to disambiguate a class named `case` from the `case` keyword by using opening and closing braces.</span></span> <span data-ttu-id="e25a3-470">Aksi takdirde, örnek hata iletisi üretir, "Anahtar kelime tanımlayıcı olarak geçerli değildir" ve derlemek için başarısız.</span><span class="sxs-lookup"><span data-stu-id="e25a3-470">Otherwise, the example would produce the error message, "Keyword is not valid as an identifier," and fail to compile.</span></span>

```vb
Public Class [case]
   Private _id As Guid
   Private name As String

   Public Sub New(name As String)
      _id = Guid.NewGuid()
      Me.name = name
   End Sub

   Public ReadOnly Property ClientName As String
      Get
         Return name
      End Get
   End Property
End Class
```

<span data-ttu-id="e25a3-471">Aşağıdaki C# örneği, tanımlayıcıyı `case` dil anahtar kelimesinden ayrıştırmak için @ simgesini kullanarak sınıfı anında atabiliyor.</span><span class="sxs-lookup"><span data-stu-id="e25a3-471">The following C# example is able to instantiate the `case` class by using the @ symbol to disambiguate the identifier from the language keyword.</span></span> <span data-ttu-id="e25a3-472">Bu olmadan, C# derleyicisi iki hata iletisi görüntüler: "Bekleneni yazın" ve "Geçersiz ifade terimi 'büyük/küçük harf'."</span><span class="sxs-lookup"><span data-stu-id="e25a3-472">Without it, the C# compiler would display two error messages, "Type expected" and "Invalid expression term 'case'."</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      @case c = new @case("John");
      Console.WriteLine(c.ClientName);
   }
}
```

### <a name="type-conversion"></a><span data-ttu-id="e25a3-473">Tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e25a3-473">Type conversion</span></span>

<span data-ttu-id="e25a3-474">Ortak Dil Belirtimi iki dönüşüm işleci tanımlar:</span><span class="sxs-lookup"><span data-stu-id="e25a3-474">The Common Language Specification defines two conversion operators:</span></span>

* <span data-ttu-id="e25a3-475">`op_Implicit`, veri veya kesinlik kaybına neden olmayan dönüşümleri genişletmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-475">`op_Implicit`, which is used for widening conversions that do not result in loss of data or precision.</span></span> <span data-ttu-id="e25a3-476">Örneğin, [Ondalık](xref:System.Decimal) yapı, integral `op_Implicit` türlerinin ve [Char](xref:System.Char) değerlerinin değerlerini `Decimal` değerlere dönüştürmek için aşırı yüklü bir işleç içerir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-476">For example, the [Decimal](xref:System.Decimal) structure includes an overloaded `op_Implicit` operator to convert values of integral types and [Char](xref:System.Char) values to `Decimal` values.</span></span>

* <span data-ttu-id="e25a3-477">`op_Explicit`, büyüklük kaybına neden olabilecek dönüşümleri daraltmak için kullanılır (bir değer daha küçük aralıklı bir değere dönüştürülür) veya kesinlik.</span><span class="sxs-lookup"><span data-stu-id="e25a3-477">`op_Explicit`, which is used for narrowing conversions that can result in loss of magnitude (a value is converted to a value that has a smaller range) or precision.</span></span> <span data-ttu-id="e25a3-478">Örneğin, `Decimal` [yapı, Çift](xref:System.Double) ve [Tek](xref:System.Single) değerleri integral değerlerine `Decimal` dönüştürmek `Decimal` ve değerleri `Double`integral `Single`değerlere dönüştürmek için aşırı yüklü `Char` `op_Explicit` bir işleç içerir, ve .</span><span class="sxs-lookup"><span data-stu-id="e25a3-478">For example, the `Decimal` structure includes an overloaded `op_Explicit` operator to convert [Double](xref:System.Double) and [Single](xref:System.Single) values to `Decimal` and to convert `Decimal` values to integral values, `Double`, `Single`, and `Char`.</span></span>

<span data-ttu-id="e25a3-479">Ancak, tüm diller operatörün aşırı yüklenmesi veya özel işleçlerin tanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e25a3-479">However, not all languages support operator overloading or the definition of custom operators.</span></span> <span data-ttu-id="e25a3-480">Bu dönüşüm işleçlerini uygulamayı seçerseniz, dönüşümü gerçekleştirmek için alternatif bir yol da sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-480">If you choose to implement these conversion operators, you should also provide an alternate way to perform the conversion.</span></span> <span data-ttu-id="e25a3-481">Xxx ve `To`Xxx `From`yöntemlerini sağlamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-481">We recommend that you provide `From`Xxx and `To`Xxx methods.</span></span>

<span data-ttu-id="e25a3-482">Aşağıdaki örnek, CLS uyumlu örtülü ve açık dönüşümleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-482">The following example defines CLS-compliant implicit and explicit conversions.</span></span> <span data-ttu-id="e25a3-483">İmzalanmış çift `UDouble` duyarlıklı, kayan nokta numarasını temsil eden bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e25a3-483">It creates a `UDouble` class that represents an signed double-precision, floating-point number.</span></span> <span data-ttu-id="e25a3-484">`UDouble` Örtülü dönüşümleri, `Double` açık dönüşümlerden `UDouble` `Single`, `Double` `UDouble` `Single` ve . `UDouble`</span><span class="sxs-lookup"><span data-stu-id="e25a3-484">It provides for implicit conversions from `UDouble` to `Double` and for explicit conversions from `UDouble` to `Single`, `Double` to `UDouble`, and `Single` to `UDouble`.</span></span> <span data-ttu-id="e25a3-485">Ayrıca, `ToDouble` bir yöntemi örtülü dönüştürme işlecine alternatif `ToSingle` `FromDouble`olarak `FromSingle` tanımlar ve açık dönüştürme işleçlerine alternatif olarak , ve yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-485">It also defines a `ToDouble` method as an alternative to the implicit conversion operator and the `ToSingle`, `FromDouble`, and `FromSingle` methods as alternatives to the explicit conversion operators.</span></span>

```csharp
using System;

public struct UDouble
{
   private double number;

   public UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public static readonly UDouble MinValue = (UDouble) 0.0;
   public static readonly UDouble MaxValue = (UDouble) Double.MaxValue;

   public static explicit operator Double(UDouble value)
   {
      return value.number;
   }

   public static implicit operator Single(UDouble value)
   {
      if (value.number > (double) Single.MaxValue)
         throw new InvalidCastException("A UDouble value is out of range of the Single type.");

      return (float) value.number;
   }

   public static explicit operator UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static implicit operator UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static Double ToDouble(UDouble value)
   {
      return (Double) value;
   }

   public static float ToSingle(UDouble value)
   {
      return (float) value;
   }

   public static UDouble FromDouble(double value)
   {
      return new UDouble(value);
   }

   public static UDouble FromSingle(float value)
   {
      return new UDouble(value);
   }
}
```

```vb
Public Structure UDouble
   Private number As Double

   Public Sub New(value As Double)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Sub New(value As Single)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Shared ReadOnly MinValue As UDouble = CType(0.0, UDouble)
   Public Shared ReadOnly MaxValue As UDouble = Double.MaxValue

   Public Shared Widening Operator CType(value As UDouble) As Double
      Return value.number
   End Operator

   Public Shared Narrowing Operator CType(value As UDouble) As Single
      If value.number > CDbl(Single.MaxValue) Then
         Throw New InvalidCastException("A UDouble value is out of range of the Single type.")
      End If
      Return CSng(value.number)
   End Operator

   Public Shared Narrowing Operator CType(value As Double) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Narrowing Operator CType(value As Single) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Function ToDouble(value As UDouble) As Double
      Return CType(value, Double)
   End Function

   Public Shared Function ToSingle(value As UDouble) As Single
      Return CType(value, Single)
   End Function

   Public Shared Function FromDouble(value As Double) As UDouble
      Return New UDouble(value)
   End Function

   Public Shared Function FromSingle(value As Single) As UDouble
      Return New UDouble(value)
   End Function
End Structure
```

### <a name="arrays"></a><span data-ttu-id="e25a3-486">Diziler</span><span class="sxs-lookup"><span data-stu-id="e25a3-486">Arrays</span></span>

<span data-ttu-id="e25a3-487">CLS uyumlu diziler aşağıdaki kurallara uygundur:</span><span class="sxs-lookup"><span data-stu-id="e25a3-487">CLS-compliant arrays conform to the following rules:</span></span>

* <span data-ttu-id="e25a3-488">Bir dizinin tüm boyutları sıfırın alt sınırı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-488">All dimensions of an array must have a lower bound of zero.</span></span> <span data-ttu-id="e25a3-489">Aşağıdaki örnek, daha düşük bir sınıra sahip CLS uyumlu olmayan bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e25a3-489">The following example creates a non-CLS-compliant array with a lower bound of one.</span></span> <span data-ttu-id="e25a3-490">[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği nin varlığına rağmen, derleyici `Numbers.GetTenPrimes` yöntem tarafından döndürülen dizi CLS uyumlu olmadığını algılamaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e25a3-490">Note that, despite the presence of the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute, the compiler does not detect that the array returned by the `Numbers.GetTenPrimes` method is not CLS-compliant.</span></span>

  ```csharp
  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static Array GetTenPrimes()
    {
        Array arr = Array.CreateInstance(typeof(Int32), new int[] {10}, new int[] {1});
        arr.SetValue(1, 1);
        arr.SetValue(2, 2);
        arr.SetValue(3, 3);
        arr.SetValue(5, 4);
        arr.SetValue(7, 5);
        arr.SetValue(11, 6);
        arr.SetValue(13, 7);
        arr.SetValue(17, 8);
        arr.SetValue(19, 9);
        arr.SetValue(23, 10);

        return arr;
    }
  }
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As Array
        Dim arr As Array = Array.CreateInstance(GetType(Int32), {10}, {1})
        arr.SetValue(1, 1)
        arr.SetValue(2, 2)
        arr.SetValue(3, 3)
        arr.SetValue(5, 4)
        arr.SetValue(7, 5)
        arr.SetValue(11, 6)
        arr.SetValue(13, 7)
        arr.SetValue(17, 8)
        arr.SetValue(19, 9)
        arr.SetValue(23, 10)
        Return arr
     End Function
  End Class
  ```

* <span data-ttu-id="e25a3-491">Tüm dizi öğeleri CLS uyumlu türlerden oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-491">All array elements must consist of CLS-compliant types.</span></span> <span data-ttu-id="e25a3-492">Aşağıdaki örnek, CLS uyumlu olmayan dizileri döndüren iki yöntem tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-492">The following example defines two methods that return non-CLS-compliant arrays.</span></span> <span data-ttu-id="e25a3-493">İlk [uint32](xref:System.UInt32) değerleri bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="e25a3-493">The first returns an array of [UInt32](xref:System.UInt32) values.</span></span> <span data-ttu-id="e25a3-494">İkinci, [Int32](xref:System.Int32) ve `UInt32` değerleri içeren bir [Nesne](xref:System.Object) dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e25a3-494">The second returns an [Object](xref:System.Object) array that includes [Int32](xref:System.Int32) and `UInt32` values.</span></span> <span data-ttu-id="e25a3-495">Derleyici, türü nedeniyle ilk diziyi uyumlu `UInt32` olmayan olarak tanımlasa da, ikinci dizinin CLS uyumlu olmayan öğeler içerdiğini fark edememektedir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-495">Although the compiler identifies the first array as non-compliant because of its `UInt32` type, it fails to recognize that the second array includes non-CLS-compliant elements.</span></span>

  ```csharp
  using System;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static UInt32[] GetTenPrimes()
    {
        uint[] arr = { 1u, 2u, 3u, 5u, 7u, 11u, 13u, 17u, 19u };
        return arr;
    }

    public static Object[] GetFivePrimes()
    {
        Object[] arr = { 1, 2, 3, 5u, 7u };
        return arr;
    }
  }
  // Compilation produces a compiler warning like the following:
  //    Array2.cs(8,27): warning CS3002: Return type of 'Numbers.GetTenPrimes()' is not
  //            CLS-compliant
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As UInt32()
        Return { 1ui, 2ui, 3ui, 5ui, 7ui, 11ui, 13ui, 17ui, 19ui }
     End Function
     Public Shared Function GetFivePrimes() As Object()
        Dim arr() As Object = { 1, 2, 3, 5ui, 7ui }
        Return arr
     End Function
  End Class
  ' Compilation produces a compiler warning like the following:
  '    warning BC40027: Return type of function 'GetTenPrimes' is not CLS-compliant.
  ```

* <span data-ttu-id="e25a3-496">Dizi parametreleri olan yöntemler için aşırı yükleme çözünürlüğü, dizi olmaları ve eleman türüne dayanır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-496">Overload resolution for methods that have array parameters is based on the fact that they are arrays and on their element type.</span></span> <span data-ttu-id="e25a3-497">Bu nedenle, aşırı yüklü `GetSquares` bir yöntemin aşağıdaki tanımı CLS uyumludur.</span><span class="sxs-lookup"><span data-stu-id="e25a3-497">For this reason, the following definition of an overloaded `GetSquares` method is CLS-compliant.</span></span>

  ```csharp
  using System;
  using System.Numerics;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static byte[] GetSquares(byte[] numbers)
    {
        byte[] numbersOut = new byte[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++) {
            int square = ((int) numbers[ctr]) * ((int) numbers[ctr]);
            if (square <= Byte.MaxValue)
                numbersOut[ctr] = (byte) square;
            // If there's an overflow, assign MaxValue to the corresponding
            // element.
            else
                numbersOut[ctr] = Byte.MaxValue;

        }
        return numbersOut;
    }

    public static BigInteger[] GetSquares(BigInteger[] numbers)
  {
        BigInteger[] numbersOut = new BigInteger[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++)
            numbersOut[ctr] = numbers[ctr] * numbers[ctr];

       return numbersOut;
    }
  }
  ```

  ```vb
  Imports System.Numerics

  <Assembly: CLSCompliant(True)>

  Public Module Numbers
     Public Function GetSquares(numbers As Byte()) As Byte()
        Dim numbersOut(numbers.Length - 1) As Byte
        For ctr As Integer = 0 To numbers.Length - 1
           Dim square As Integer = (CInt(numbers(ctr)) * CInt(numbers(ctr)))
           If square <= Byte.MaxValue Then
              numbersOut(ctr) = CByte(square)
           ' If there's an overflow, assign MaxValue to the corresponding
           ' element.
           Else
              numbersOut(ctr) = Byte.MaxValue
           End If
        Next
        Return numbersOut
     End Function

     Public Function GetSquares(numbers As BigInteger()) As BigInteger()
         Dim numbersOut(numbers.Length - 1) As BigInteger
         For ctr As Integer = 0 To numbers.Length - 1
            numbersOut(ctr) = numbers(ctr) * numbers(ctr)
         Next
         Return numbersOut
     End Function
  End Module
  ```

### <a name="interfaces"></a><span data-ttu-id="e25a3-498">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="e25a3-498">Interfaces</span></span>

<span data-ttu-id="e25a3-499">CLS uyumlu arabirimler özellikleri, olayları ve sanal yöntemleri (uygulama olmadan yöntemler) tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-499">CLS-compliant interfaces can define properties, events, and virtual methods (methods with no implementation).</span></span> <span data-ttu-id="e25a3-500">CLS uyumlu bir arabirim aşağıdakilerden herhangi biri olamaz:</span><span class="sxs-lookup"><span data-stu-id="e25a3-500">A CLS-compliant interface cannot have any of the following:</span></span>

* <span data-ttu-id="e25a3-501">Statik yöntemler veya statik alanlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-501">Static methods or static fields.</span></span> <span data-ttu-id="e25a3-502">Bir arabirimde statik bir üye tanımlarsanız C# derleyicisi derleyici hataları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e25a3-502">The C# compiler generates compiler errors if you define a static member in an interface.</span></span>

* <span data-ttu-id="e25a3-503">Alanları.</span><span class="sxs-lookup"><span data-stu-id="e25a3-503">Fields.</span></span> <span data-ttu-id="e25a3-504">C# derleyicisi, arabirimdeki bir alanı tanımlarsanız derleyici hataları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e25a3-504">The C# a compiler generates compiler errors if you define a field in an interface.</span></span>

* <span data-ttu-id="e25a3-505">CLS uyumlu olmayan yöntemler.</span><span class="sxs-lookup"><span data-stu-id="e25a3-505">Methods that are not CLS-compliant.</span></span> <span data-ttu-id="e25a3-506">Örneğin, aşağıdaki arabirim tanımı, `INumber.GetUnsigned`CLS uyumlu olmayan olarak işaretlenmiş bir yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-506">For example, the following interface definition includes a method, `INumber.GetUnsigned`, that is marked as non-CLS-compliant.</span></span> <span data-ttu-id="e25a3-507">Bu örnek derleyici uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e25a3-507">This example generates a compiler warning.</span></span>

  ```csharp
  using System;

  [assembly:CLSCompliant(true)]

  public interface INumber
  {
      int Length();
      [CLSCompliant(false)] ulong GetUnsigned();
  }
  // Attempting to compile the example displays output like the following:
  //    Interface2.cs(8,32): warning CS3010: 'INumber.GetUnsigned()': CLS-compliant interfaces
  //            must have only CLS-compliant members
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Interface INumber
    Function Length As Integer
      <CLSCompliant(False)> Function GetUnsigned As ULong
    End Interface
    ' Attempting to compile the example displays output like the following:
    '    Interface2.vb(9) : warning BC40033: Non CLS-compliant 'function' is not allowed in a
    '    CLS-compliant interface.
    '
    '       <CLSCompliant(False)> Function GetUnsigned As ULong
    '                                      ~~~~~~~~~~~
  ```

  <span data-ttu-id="e25a3-508">Bu kural nedeniyle, CLS uyumlu olmayan üyeleri uygulamak için CLS uyumlu türleri gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e25a3-508">Because of this rule, CLS-compliant types are not required to implement non-CLS-compliant members.</span></span> <span data-ttu-id="e25a3-509">CLS uyumlu bir çerçeve, CLS uyumlu olmayan bir arabirim uygulayan bir sınıfı ortaya çıkarırsa, CLS uyumlu olmayan tüm üyelerin somut uygulamalarını da sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-509">If a CLS-compliant framework does expose a class that implements a non-CLS compliant interface, it should also provide concrete implementations of all non-CLS-compliant members.</span></span>

<span data-ttu-id="e25a3-510">CLS uyumlu dil derleyicileri, bir sınıfın birden çok arabirimde aynı ad ve imzaya sahip üyelerin ayrı uygulamalarını sağlamasına da izin vermelidir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-510">CLS-compliant language compilers must also allow a class to provide separate implementations of members that have the same name and signature in multiple interfaces.</span></span> <span data-ttu-id="e25a3-511">C# aynı adlı yöntemlerin farklı uygulamaları sağlamak için açık arabirim uygulamalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="e25a3-511">C# supports explicit interface implementations to provide different implementations of identically named methods.</span></span> <span data-ttu-id="e25a3-512">Aşağıdaki örnek, açık arabirim uygulamaları `Temperature` olarak ve `ICelsius` `IFahrenheit` arabirimleri uygulayan bir sınıf tanımlayarak bu senaryoyu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-512">The following example illustrates this scenario by defining a `Temperature` class that implements the `ICelsius` and `IFahrenheit` interfaces as explicit interface implementations.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public interface IFahrenheit
{
   decimal GetTemperature();
}

public interface ICelsius
{
   decimal GetTemperature();
}

public class Temperature : ICelsius, IFahrenheit
{
   private decimal _value;

   public Temperature(decimal value)
   {
      // We assume that this is the Celsius value.
      _value = value;
   }

   decimal IFahrenheit.GetTemperature()
   {
      return _value * 9 / 5 + 32;
   }

   decimal ICelsius.GetTemperature()
   {
      return _value;
   }
}
public class Example
{
   public static void Main()
   {
      Temperature temp = new Temperature(100.0m);
      ICelsius cTemp = temp;
      IFahrenheit fTemp = temp;
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        cTemp.GetTemperature());
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        fTemp.GetTemperature());
   }
}
// The example displays the following output:
//       Temperature in Celsius: 100.0 degrees
//       Temperature in Fahrenheit: 212.0 degrees
```

```vb
Assembly: CLSCompliant(True)>

Public Interface IFahrenheit
   Function GetTemperature() As Decimal
End Interface

Public Interface ICelsius
   Function GetTemperature() As Decimal
End Interface

Public Class Temperature : Implements ICelsius, IFahrenheit
   Private _value As Decimal

   Public Sub New(value As Decimal)
      ' We assume that this is the Celsius value.
      _value = value
   End Sub

   Public Function GetFahrenheit() As Decimal _
          Implements IFahrenheit.GetTemperature
      Return _value * 9 / 5 + 32
   End Function

   Public Function GetCelsius() As Decimal _
          Implements ICelsius.GetTemperature
      Return _value
   End Function
End Class

Module Example
   Public Sub Main()
      Dim temp As New Temperature(100.0d)
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        temp.GetCelsius())
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        temp.GetFahrenheit())
   End Sub
End Module
' The example displays the following output:
'       Temperature in Celsius: 100.0 degrees
'       Temperature in Fahrenheit: 212.0 degrees
```

### <a name="enumerations"></a><span data-ttu-id="e25a3-513">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="e25a3-513">Enumerations</span></span>

<span data-ttu-id="e25a3-514">CLS uyumlu sayısallaştırmalar aşağıdaki kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="e25a3-514">CLS-compliant enumerations must follow these rules:</span></span>

* <span data-ttu-id="e25a3-515">Numaralandırmanın altında yatan tip içsel BIR CLS uyumlu bir toplam[(Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), veya [Int64](xref:System.Int64)) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-515">The underlying type of the enumeration must be an intrinsic CLS-compliant integer ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), or [Int64](xref:System.Int64)).</span></span> <span data-ttu-id="e25a3-516">Örneğin, aşağıdaki kod, temel türü [UInt32](xref:System.UInt32) olan bir numaralandırma tanımlamaya çalışır ve derleyici uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e25a3-516">For example, the following code tries to define an enumeration whose underlying type is [UInt32](xref:System.UInt32) and generates a compiler warning.</span></span>

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public enum Size : uint {
        Unspecified = 0,
        XSmall = 1,
        Small = 2,
        Medium = 3,
        Large = 4,
        XLarge = 5
    };

    public class Clothing
    {
        public string Name;
        public string Type;
        public string Size;
    }
    // The attempt to compile the example displays a compiler warning like the following:
    //    Enum3.cs(6,13): warning CS3009: 'Size': base type 'uint' is not CLS-compliant
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Enum Size As UInt32
       Unspecified = 0
       XSmall = 1
       Small = 2
       Medium = 3
       Large = 4
       XLarge = 5
    End Enum

    Public Class Clothing
       Public Name As String
       Public Type As String
       Public Size As Size
    End Class
    ' The attempt to compile the example displays a compiler warning like the following:
    '    Enum3.vb(6) : warning BC40032: Underlying type 'UInt32' of Enum is not CLS-compliant.
    '
    '    Public Enum Size As UInt32
    '                ~~~~
    ```

* <span data-ttu-id="e25a3-517">Bir numaralandırma türü öznitelik ile `Value__` `FieldAttributes.RTSpecialName` işaretlenmiş tek bir örnek alanı adlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-517">An enumeration type must have a single instance field named `Value__` that is marked with the `FieldAttributes.RTSpecialName` attribute.</span></span> <span data-ttu-id="e25a3-518">Bu, alan değerini dolaylı olarak referans almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-518">This enables you to reference the field value implicitly.</span></span>

* <span data-ttu-id="e25a3-519">Numaralandırma, türleri numaralandırmanın kendisiyle eşleşen gerçek statik alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-519">An enumeration includes literal static fields whose types match the type of the enumeration itself.</span></span> <span data-ttu-id="e25a3-520">Örneğin, `State` `State.On` bir numaralandırma ve `State.Off`, her `State.On` `State.Off` ikisi de türü `State`.</span><span class="sxs-lookup"><span data-stu-id="e25a3-520">For example, if you define a `State` enumeration with values of `State.On` and `State.Off`, `State.On` and `State.Off` are both literal static fields whose type is `State`.</span></span>

* <span data-ttu-id="e25a3-521">İki tür sayısallaştırma vardır:</span><span class="sxs-lookup"><span data-stu-id="e25a3-521">There are two kinds of enumerations:</span></span>

  * <span data-ttu-id="e25a3-522">Birbirini dışlayan, tamsayı değerleri kümesini temsil eden numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="e25a3-522">An enumeration that represents a set of mutually exclusive, named integer values.</span></span> <span data-ttu-id="e25a3-523">Bu tür numaralandırma [System.FlagsAttribute](xref:System.FlagsAttribute) özel özniteliği yokluğu ile gösterilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-523">This type of enumeration is indicated by the absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>

  * <span data-ttu-id="e25a3-524">Adsız bir değer oluşturmak için biraraya getirebilen bit bayrakları kümesini temsil eden numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="e25a3-524">An enumeration that represents a set of bit flags that can combine to generate an unnamed value.</span></span> <span data-ttu-id="e25a3-525">Bu tür numaralandırma [System.FlagsAttribute](xref:System.FlagsAttribute) özel özniteliği varlığı ile gösterilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-525">This type of enumeration is indicated by the presence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>

<span data-ttu-id="e25a3-526">Daha fazla bilgi için [Enum](xref:System.Enum) yapısıiçin belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="e25a3-526">For more information, see the documentation for the [Enum](xref:System.Enum) structure.</span></span>

* <span data-ttu-id="e25a3-527">Numaralandırmanın değeri, belirtilen değerlerin aralığıyla sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-527">The value of an enumeration is not limited to the range of its specified values.</span></span> <span data-ttu-id="e25a3-528">Başka bir deyişle, numaralandırmadaki değer aralığı, temel değerinin aralığıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-528">In other words, the range of values in an enumeration is the range of its underlying value.</span></span> <span data-ttu-id="e25a3-529">Belirtilen değerin `Enum.IsDefined` numaralandırmanın bir üyesi olup olmadığını belirlemek için yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-529">You can use the `Enum.IsDefined` method to determine whether a specified value is a member of an enumeration.</span></span>

### <a name="type-members-in-general"></a><span data-ttu-id="e25a3-530">Genel olarak tip üyeleri</span><span class="sxs-lookup"><span data-stu-id="e25a3-530">Type members in general</span></span>

<span data-ttu-id="e25a3-531">Ortak Dil Belirtimi, tüm alanların ve yöntemlerin belirli bir sınıfın üyesi olarak erişilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-531">The Common Language Specification requires all fields and methods to be accessed as members of a particular class.</span></span> <span data-ttu-id="e25a3-532">Bu nedenle, genel statik alanlar ve yöntemler (diğer bir şekilde statik alanlar veya bir tür dışında tanımlanan yöntemler) CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-532">Therefore, global static fields and methods (that is, static fields or methods that are defined apart from a type) are not CLS-compliant.</span></span> <span data-ttu-id="e25a3-533">Kaynak kodunuza genel bir alan veya yöntem eklemeye çalışırsanız, C# derleyicisi bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e25a3-533">If you try to include a global field or method in your source code, the C# compiler generates a compiler error.</span></span>

<span data-ttu-id="e25a3-534">Ortak Dil Belirtimi yalnızca standart yönetilen arama kuralını destekler.</span><span class="sxs-lookup"><span data-stu-id="e25a3-534">The Common Language Specification supports only the standard managed calling convention.</span></span> <span data-ttu-id="e25a3-535">`varargs` Anahtar kelimeyle işaretlenmiş değişken bağımsız değişken listeleriyle yönetilmeyen çağrı kurallarını ve yöntemlerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e25a3-535">It doesn't support unmanaged calling conventions and methods with variable argument lists marked with the `varargs` keyword.</span></span> <span data-ttu-id="e25a3-536">Standart yönetilen arama kuralıyla uyumlu değişken bağımsız değişken listeleri [için, ParamArrayAttribute](xref:System.ParamArrayAttribute) özniteliğini veya `params` C#'daki anahtar `ParamArray` kelime ve Visual Basic'teki anahtar sözcük gibi tek tek dilin uygulamasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e25a3-536">For variable argument lists that are compatible with the standard managed calling convention, use the [ParamArrayAttribute](xref:System.ParamArrayAttribute) attribute or the individual language's implementation, such as the `params` keyword in C# and the `ParamArray` keyword in Visual Basic.</span></span>

### <a name="member-accessibility"></a><span data-ttu-id="e25a3-537">Üye erişilebilirliği</span><span class="sxs-lookup"><span data-stu-id="e25a3-537">Member accessibility</span></span>

<span data-ttu-id="e25a3-538">Devralınan bir üyenin geçersiz kılınması, bu üyenin erişilebilirliğini değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="e25a3-538">Overriding an inherited member cannot change the accessibility of that member.</span></span> <span data-ttu-id="e25a3-539">Örneğin, taban sınıftaki ortak yöntem, türemiş bir sınıftaki özel bir yöntem tarafından geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-539">For example, a public method in a base class cannot be overridden by a private method in a derived class.</span></span> <span data-ttu-id="e25a3-540">Bir istisna vardır: `protected internal` (C#' `Protected Friend` da) veya (Visual Basic'te) üye, farklı bir derlemedeki bir tür tarafından geçersiz kılınan bir derlemede.</span><span class="sxs-lookup"><span data-stu-id="e25a3-540">There is one exception: a `protected internal` (in C#) or `Protected Friend` (in Visual Basic) member in one assembly that is overridden by a type in a different assembly.</span></span>  <span data-ttu-id="e25a3-541">Bu durumda, geçersiz kılmanın `Protected`erişilebilirliği.</span><span class="sxs-lookup"><span data-stu-id="e25a3-541">In that case, the accessibility of the override is `Protected`.</span></span>

<span data-ttu-id="e25a3-542">Aşağıdaki örnek, [CLSCompliant Attribute özniteliği](xref:System.CLSCompliantAttribute) ayarlandığında `true`oluşturulan hatayı göstermektedir `Person`ve türetilen bir `Animal`sınıf olan , `Species` özelliğin erişilebilirliğini ortaktan özele değiştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-542">The following example illustrates the error that is generated when the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is set to `true`, and `Person`, which is a class derived from `Animal`, tries to change the accessibility of the `Species` property from public to private.</span></span> <span data-ttu-id="e25a3-543">Erişilebilirliği genel olarak değiştirilirse, örnek başarıyla derlenir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-543">The example compiles successfully if its accessibility is changed to public.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Animal
{
   private string _species;

   public Animal(string species)
   {
      _species = species;
   }

   public virtual string Species
   {
      get { return _species; }
   }

   public override string ToString()
   {
      return _species;
   }
}

public class Human : Animal
{
   private string _name;

   public Human(string name) : base("Homo Sapiens")
   {
      _name = name;
   }

   public string Name
   {
      get { return _name; }
   }

   private override string Species
   {
      get { return base.Species; }
   }

   public override string ToString()
   {
      return _name;
   }
}

public class Example
{
   public static void Main()
   {
      Human p = new Human("John");
      Console.WriteLine(p.Species);
      Console.WriteLine(p.ToString());
   }
}
// The example displays the following output:
//    error CS0621: 'Human.Species': virtual or abstract members cannot be private
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Animal
   Private _species As String

   Public Sub New(species As String)
      _species = species
   End Sub

   Public Overridable ReadOnly Property Species As String
      Get
         Return _species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _species
   End Function
End Class

Public Class Human : Inherits Animal
   Private _name As String

   Public Sub New(name As String)
      MyBase.New("Homo Sapiens")
      _name = name
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return _name
      End Get
   End Property

   Private Overrides ReadOnly Property Species As String
      Get
         Return MyBase.Species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _name
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim p As New Human("John")
      Console.WriteLine(p.Species)
      Console.WriteLine(p.ToString())
   End Sub
End Module
' The example displays the following output:
'     'Private Overrides ReadOnly Property Species As String' cannot override
'     'Public Overridable ReadOnly Property Species As String' because
'      they have different access levels.
'
'         Private Overrides ReadOnly Property Species As String
```

<span data-ttu-id="e25a3-544">Bir üyenin imzasındaki türlere, bu üyeye erişilebildiğinde erişilebiliyor olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-544">Types in the signature of a member must be accessible whenever that member is accessible.</span></span> <span data-ttu-id="e25a3-545">Örneğin, bu, ortak bir üyenin türü özel, korumalı veya dahili bir parametre içeremeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-545">For example, this means that a public member cannot include a parameter whose type is private, protected, or internal.</span></span> <span data-ttu-id="e25a3-546">Aşağıdaki örnekte, bir sınıf oluşturucusu `StringWrapper` dize değerinin nasıl `StringOperationType` paketlendiğini belirleyen bir iç numaralandırma değerini ortaya çıkardığında ortaya çıkan derleyici hatasını gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-546">The following example illustrates the compiler error that results when a `StringWrapper` class constructor exposes an internal `StringOperationType` enumeration value that determines how a string value should be wrapped.</span></span>

```csharp
using System;
using System.Text;

public class StringWrapper
{
   string internalString;
   StringBuilder internalSB = null;
   bool useSB = false;

   public StringWrapper(StringOperationType type)
   {
      if (type == StringOperationType.Normal) {
         useSB = false;
      }
      else {
         useSB = true;
         internalSB = new StringBuilder();
      }
   }

   // The remaining source code...
}

internal enum StringOperationType { Normal, Dynamic }
// The attempt to compile the example displays the following output:
//    error CS0051: Inconsistent accessibility: parameter type
//            'StringOperationType' is less accessible than method
//            'StringWrapper.StringWrapper(StringOperationType)'
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class StringWrapper

   Dim internalString As String
   Dim internalSB As StringBuilder = Nothing
   Dim useSB As Boolean = False

   Public Sub New(type As StringOperationType)
      If type = StringOperationType.Normal Then
         useSB = False
      Else
         internalSB = New StringBuilder()
         useSB = True
      End If
   End Sub

   ' The remaining source code...
End Class

Friend Enum StringOperationType As Integer
   Normal = 0
   Dynamic = 1
End Enum
' The attempt to compile the example displays the following output:
'    error BC30909: 'type' cannot expose type 'StringOperationType'
'     outside the project through class 'StringWrapper'.
'
'       Public Sub New(type As StringOperationType)
'                              ~~~~~~~~~~~~~~~~~~~
```

### <a name="generic-types-and-members"></a><span data-ttu-id="e25a3-547">Genel türler ve üyeler</span><span class="sxs-lookup"><span data-stu-id="e25a3-547">Generic types and members</span></span>

<span data-ttu-id="e25a3-548">İç içe geçmiş türler her zaman en az kendi çevreleyen türü kadar sayıda genel parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-548">Nested types always have at least as many generic parameters as their enclosing type.</span></span> <span data-ttu-id="e25a3-549">Bunlar, çevreleyen türdeki genel parametrelere göre konumolarak karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-549">These correspond by position to the generic parameters in the enclosing type.</span></span> <span data-ttu-id="e25a3-550">Genel tür, yeni genel parametreler de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-550">The generic type can also include new generic parameters.</span></span>

<span data-ttu-id="e25a3-551">İçeren bir türün genel tür parametreleri ile iç içe olan türleri arasındaki ilişki, tek tek dillerin sözdizimi tarafından gizlenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-551">The relationship between the generic type parameters of a containing type and its nested types may be hidden by the syntax of individual languages.</span></span> <span data-ttu-id="e25a3-552">Aşağıdaki örnekte, genel `Outer<T>` bir tür iki `Inner1A` iç `Inner1B<U>`içe sınıf içerir ve.</span><span class="sxs-lookup"><span data-stu-id="e25a3-552">In the following example, a generic type `Outer<T>` contains two nested classes, `Inner1A` and `Inner1B<U>`.</span></span> <span data-ttu-id="e25a3-553">Her sınıfın `ToString` devraldığı yönteme yapılan `Object.ToString`çağrılar, iç içe geçen her sınıfın kendi sınıfının tür parametrelerini içerdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-553">The calls to the `ToString` method, which each class inherits from `Object.ToString`, show that each nested class includes the type parameters of its containing class.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Outer<T>
{
   T value;

   public Outer(T value)
   {
      this.value = value;
   }

   public class Inner1A : Outer<T>
   {
      public Inner1A(T value) : base(value)
      {  }
   }

   public class Inner1B<U> : Outer<T>
   {
      U value2;

      public Inner1B(T value1, U value2) : base(value1)
      {
         this.value2 = value2;
      }
   }
}

public class Example
{
   public static void Main()
   {
      var inst1 = new Outer<String>("This");
      Console.WriteLine(inst1);

      var inst2 = new Outer<String>.Inner1A("Another");
      Console.WriteLine(inst2);

      var inst3 = new Outer<String>.Inner1B<int>("That", 2);
      Console.WriteLine(inst3);
   }
}
// The example displays the following output:
//       Outer`1[System.String]
//       Outer`1+Inner1A[System.String]
//       Outer`1+Inner1B`1[System.String,System.Int32]
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Outer(Of T)
   Dim value As T

   Public Sub New(value As T)
      Me.value = value
   End Sub

   Public Class Inner1A : Inherits Outer(Of T)
      Public Sub New(value As T)
         MyBase.New(value)
      End Sub
   End Class

   Public Class Inner1B(Of U) : Inherits Outer(Of T)
      Dim value2 As U

      Public Sub New(value1 As T, value2 As U)
         MyBase.New(value1)
         Me.value2 = value2
      End Sub
   End Class
End Class

Public Module Example
   Public Sub Main()
      Dim inst1 As New Outer(Of String)("This")
      Console.WriteLine(inst1)

      Dim inst2 As New Outer(Of String).Inner1A("Another")
      Console.WriteLine(inst2)

      Dim inst3 As New Outer(Of String).Inner1B(Of Integer)("That", 2)
      Console.WriteLine(inst3)
   End Sub
End Module
' The example displays the following output:
'       Outer`1[System.String]
'       Outer`1+Inner1A[System.String]
'       Outer`1+Inner1B`1[System.String,System.Int32]
```

<span data-ttu-id="e25a3-554">Genel tür adları form *adı*'*n*, *burada ad* türü *\`* adı, bir karakter literal ve *n* türü üzerinde bildirilen parametrelerin sayısı veya iç içe genel türleri için, yeni tanıtılan tür parametrelerinin sayısı kodlanır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-554">Generic type names are encoded in the form *name*'*n*, where *name* is the type name, *\`* is a character literal, and *n* is the number of parameters declared on the type, or, for nested generic types, the number of newly introduced type parameters.</span></span> <span data-ttu-id="e25a3-555">Genel tür adlarının bu kodlaması, öncelikle bir kitaplıktaki CLS şikayeti genel türlerine erişmek için yansımayı kullanan geliştiricilerin ilgisini çekmiştir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-555">This encoding of generic type names is primarily of interest to developers who use reflection to access CLS-complaint generic types in a library.</span></span>

<span data-ttu-id="e25a3-556">Genel bir türe kısıtlamalar uygulanırsa, kısıtlama olarak kullanılan tüm türler de CLS uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-556">If constraints are applied to a generic type, any types used as constraints must also be CLS-compliant.</span></span> <span data-ttu-id="e25a3-557">Aşağıdaki örnek, CLS `BaseClass` uyumlu olmayan bir sınıf ve `BaseCollection` tür `BaseClass`parametresi.</span><span class="sxs-lookup"><span data-stu-id="e25a3-557">The following example defines a class named `BaseClass` that is not CLS-compliant and a generic class named `BaseCollection` whose type parameter must derive from `BaseClass`.</span></span> <span data-ttu-id="e25a3-558">`BaseClass` Ancak CLS uyumlu olmadığından, derleyici bir uyarı yayar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-558">But because `BaseClass` is not CLS-compliant, the compiler emits a warning.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

[CLSCompliant(false)] public class BaseClass
{}

public class BaseCollection<T> where T : BaseClass
{}
// Attempting to compile the example displays the following output:
//    warning CS3024: Constraint type 'BaseClass' is not CLS-compliant
```

```vb
Assembly: CLSCompliant(True)>

<CLSCompliant(False)> Public Class BaseClass
End Class

Public Class BaseCollection(Of T As BaseClass)
End Class
' Attempting to compile the example displays the following output:
'    warning BC40040: Generic parameter constraint type 'BaseClass' is not
'    CLS-compliant.
'
'    Public Class BaseCollection(Of T As BaseClass)
'                                        ~~~~~~~~~
```

<span data-ttu-id="e25a3-559">Genel bir tür genel bir taban türünden türetilmişse, temel türdeki kısıtlamaların da karşılanmasına engel olabilmesi için kısıtlamaları yeniden beyan etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-559">If a generic type is derived from a generic base type, it must redeclare any constraints so that it can guarantee that constraints on the base type are also satisfied.</span></span> <span data-ttu-id="e25a3-560">Aşağıdaki örnek, herhangi `Number<T>` bir sayısal türü temsil eden bir tanım tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-560">The following example defines a `Number<T>` that can represent any numeric type.</span></span> <span data-ttu-id="e25a3-561">Ayrıca kayan `FloatingPoint<T>` nokta değerini temsil eden bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-561">It also defines a `FloatingPoint<T>` class that represents a floating point value.</span></span> <span data-ttu-id="e25a3-562">Ancak, kaynak kod derlenemiyor, çünkü `Number<T>` `FloatingPoint<T>`bu kısıtlamayı (T'nin bir değer türü olması gerekir) .</span><span class="sxs-lookup"><span data-stu-id="e25a3-562">However, the source code fails to compile, because it does not apply the constraint on `Number<T>` (that T must be a value type) to `FloatingPoint<T>`.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T>
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
// The attempt to compile the example displays the following output:
//       error CS0453: The type 'T' must be a non-nullable value type in
//               order to use it as parameter 'T' in the generic type or method 'Number<T>'
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
' The attempt to compile the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

<span data-ttu-id="e25a3-563">Kısıtlama `FloatingPoint<T>` sınıfa eklenirse, örnek başarıyla derlenir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-563">The example compiles successfully if the constraint is added to the `FloatingPoint<T>` class.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T> where T : struct
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T As Structure) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
```

<span data-ttu-id="e25a3-564">Ortak Dil Belirtimi iç içe gelen türler ve korunan üyeler için uygun bir anlık hareket modeli uygular.</span><span class="sxs-lookup"><span data-stu-id="e25a3-564">The Common Language Specification imposes a conservative per-instantiation model for nested types and protected members.</span></span> <span data-ttu-id="e25a3-565">Açık genel türler, iç içe, korumalı genel bir türbelirli bir anlık içeren imzaları olan alanları veya üyeleri ortaya çıkaramaz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-565">Open generic types cannot expose fields or members with signatures that contain a specific instantiation of a nested, protected generic type.</span></span> <span data-ttu-id="e25a3-566">Genel bir taban sınıfının veya arabirimin belirli bir anlık anını genişleten genel olmayan türler, iç içe, korunan genel türün farklı bir anlık anlık bir anını içeren imzalarla alanları veya üyeleri ortaya çıkaramaz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-566">Non-generic types that extend a specific instantiation of a generic base class or interface cannot expose fields or members with signatures that contain a different instantiation of a nested, protected generic type.</span></span>

<span data-ttu-id="e25a3-567">Aşağıdaki örnek, `C1<T>`genel bir türü ve korumalı `C1<T>.N`bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-567">The following example defines a generic type, `C1<T>`, and a protected class, `C1<T>.N`.</span></span> <span data-ttu-id="e25a3-568">`C1<T>`iki yöntemi `M1` vardır `M2`ve .</span><span class="sxs-lookup"><span data-stu-id="e25a3-568">`C1<T>` has two methods, `M1` and `M2`.</span></span> <span data-ttu-id="e25a3-569">Ancak, `M1` bir `C1<int>.N` nesneyi ' den döndürmeye çalıştığından `C1<T>`CLS uyumlu değildir</span><span class="sxs-lookup"><span data-stu-id="e25a3-569">However, `M1` is not CLS-compliant because it tries to return a `C1<int>.N` object from `C1<T>`.</span></span> <span data-ttu-id="e25a3-570">İkinci sınıf, `C2` `C1<long>`türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-570">A second class, `C2`, is derived from `C1<long>`.</span></span> <span data-ttu-id="e25a3-571">İki yöntemi var `M3` `M4`ve.</span><span class="sxs-lookup"><span data-stu-id="e25a3-571">It has two methods, `M3` and `M4`.</span></span> <span data-ttu-id="e25a3-572">`M3`bir `C1<int>.N` nesneyi bir alt sınıftan döndürmeye çalıştığından `C1<long>`CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-572">`M3` is not CLS-compliant because it tries to return a `C1<int>.N` object from a subclass of `C1<long>`.</span></span> <span data-ttu-id="e25a3-573">Dil derleyicilerin daha da kısıtlayıcı olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e25a3-573">Note that language compilers can be even more restrictive.</span></span> <span data-ttu-id="e25a3-574">Bu örnekte, Visual Basic derlemeye çalıştığında `M4`bir hata görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e25a3-574">In this example, Visual Basic displays an error when it tries to compile `M4`.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class C1<T>
{
   protected class N { }

   protected void M1(C1<int>.N n) { } // Not CLS-compliant - C1<int>.N not
                                      // accessible from within C1<T> in all
                                      // languages
   protected void M2(C1<T>.N n) { }   // CLS-compliant – C1<T>.N accessible
                                      // inside C1<T>
}

public class C2 : C1<long>
{
   protected void M3(C1<int>.N n) { }  // Not CLS-compliant – C1<int>.N is not
                                       // accessible in C2 (extends C1<long>)

   protected void M4(C1<long>.N n) { } // CLS-compliant, C1<long>.N is
                                       // accessible in C2 (extends C1<long>)
}
// Attempting to compile the example displays output like the following:
//       Generics4.cs(9,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
//       Generics4.cs(18,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
```

```vb
<Assembly:CLSCompliant(True)>

Public Class C1(Of T)
   Protected Class N
   End Class

   Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
                                             ' accessible from within C1(Of T) in all
   End Sub                                   ' languages

   Protected Sub M2(n As C1(Of T).N)     ' CLS-compliant – C1(Of T).N accessible
   End Sub                               ' inside C1(Of T)
End Class

Public Class C2 : Inherits C1(Of Long)
   Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant – C1(Of Integer).N is not
   End Sub                                   ' accessible in C2 (extends C1(Of Long))

   Protected Sub M4(n As C1(Of Long).N)
   End Sub
End Class
' Attempting to compile the example displays output like the following:
'    error BC30508: 'n' cannot expose type 'C1(Of Integer).N' in namespace
'    '<Default>' through class 'C1'.
'
'       Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
'                             ~~~~~~~~~~~~~~~~
'    error BC30389: 'C1(Of T).N' is not accessible in this context because
'    it is 'Protected'.
'
'       Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant - C1(Of Integer).N is not
'
'                             ~~~~~~~~~~~~~~~~
'
'    error BC30389: 'C1(Of T).N' is not accessible in this context because it is 'Protected'.
'
'       Protected Sub M4(n As C1(Of Long).N)
'                             ~~~~~~~~~~~~~
```

### <a name="constructors"></a><span data-ttu-id="e25a3-575">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="e25a3-575">Constructors</span></span>

<span data-ttu-id="e25a3-576">CLS uyumlu sınıflarda ve yapılardaki kurucular aşağıdaki kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="e25a3-576">Constructors in CLS-compliant classes and structures must follow these rules:</span></span>

* <span data-ttu-id="e25a3-577">Türetilmiş bir sınıfın oluşturucusu, devralınan örnek verilerine erişmeden önce taban sınıfının örnek oluşturucuyu çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-577">A constructor of a derived class must call the instance constructor of its base class before it accesses inherited instance data.</span></span> <span data-ttu-id="e25a3-578">Bu gereksinim, taban sınıf oluşturucuların türetilmiş sınıfları tarafından devralınmaması nedeniyledir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-578">This requirement is due to the fact that base class constructors are not inherited by their derived classes.</span></span> <span data-ttu-id="e25a3-579">Bu kural, doğrudan devralmayı desteklemeyen yapılar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-579">This rule does not apply to structures, which do not support direct inheritance.</span></span>

  <span data-ttu-id="e25a3-580">Genellikle derleyiciler, aşağıdaki örnekte görüldüğü gibi, bu kuralı CLS uyumluluğundan bağımsız olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="e25a3-580">Typically, compilers enforce this rule independently of CLS compliance, as the following example shows.</span></span> <span data-ttu-id="e25a3-581">Bir sınıftan `Doctor` türetilen bir `Person` sınıf oluşturur, `Doctor` ancak sınıf, `Person` devralınan örnek alanlarını başlatmaya sınıf oluşturucusu çağıramaz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-581">It creates a `Doctor` class that is derived from a `Person` class, but the `Doctor` class fails to call the `Person` class constructor to initialize inherited instance fields.</span></span>

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public class Person
    {
    private string fName, lName, _id;

    public Person(string firstName, string lastName, string id)
    {
        if (String.IsNullOrEmpty(firstName + lastName))
            throw new ArgumentNullException("Either a first name or a last name must be provided.");

        fName = firstName;
        lName = lastName;
        _id = id;
    }

    public string FirstName
    {
        get { return fName; }
    }

    public string LastName
    {
        get { return lName; }
    }

    public string Id
    {
        get { return _id; }
    }

    public override string ToString()
    {
        return String.Format("{0}{1}{2}", fName,
                            String.IsNullOrEmpty(fName) ?  "" : " ",
                            lName);
    }
    }

    public class Doctor : Person
    {
    public Doctor(string firstName, string lastName, string id)
    {
    }

    public override string ToString()
    {
        return "Dr. " + base.ToString();
    }
    }
    // Attempting to compile the example displays output like the following:
    //    ctor1.cs(45,11): error CS1729: 'Person' does not contain a constructor that takes 0
    //            arguments
    //    ctor1.cs(10,11): (Location of symbol related to previous error)
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Class Person
       Private fName, lName, _id As String

       Public Sub New(firstName As String, lastName As String, id As String)
          If String.IsNullOrEmpty(firstName + lastName) Then
             Throw New ArgumentNullException("Either a first name or a last name must be provided.")
          End If

          fName = firstName
          lName = lastName
          _id = id
       End Sub

       Public ReadOnly Property FirstName As String
          Get
             Return fName
          End Get
       End Property

       Public ReadOnly Property LastName As String
          Get
             Return lName
          End Get
       End Property

       Public ReadOnly Property Id As String
          Get
             Return _id
          End Get
       End Property

       Public Overrides Function ToString() As String
          Return String.Format("{0}{1}{2}", fName,
                               If(String.IsNullOrEmpty(fName), "", " "),
                               lName)
       End Function
    End Class

    Public Class Doctor : Inherits Person
       Public Sub New(firstName As String, lastName As String, id As String)
       End Sub

       Public Overrides Function ToString() As String
          Return "Dr. " + MyBase.ToString()
       End Function
    End Class
    ' Attempting to compile the example displays output like the following:
    '    Ctor1.vb(46) : error BC30148: First statement of this 'Sub New' must be a call
    '    to 'MyBase.New' or 'MyClass.New' because base class 'Person' of 'Doctor' does
    '    not have an accessible 'Sub New' that can be called with no arguments.
    '
    '       Public Sub New()
    '                  ~~~
    ````

* <span data-ttu-id="e25a3-582">Nesne oluşturucu, nesne oluşturmak dışında çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-582">An object constructor cannot be called except to create an object.</span></span> <span data-ttu-id="e25a3-583">Ayrıca, bir nesne iki kez başharfe alınamaz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-583">In addition, an object cannot be initialized twice.</span></span> <span data-ttu-id="e25a3-584">Örneğin, bu yapıcılar `Object.MemberwiseClone` çağırmamak gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-584">For example, this means that `Object.MemberwiseClone` must not call constructors.</span></span>

### <a name="properties"></a><span data-ttu-id="e25a3-585">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-585">Properties</span></span>

<span data-ttu-id="e25a3-586">CLS uyumlu türlerdeki özellikler aşağıdaki kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="e25a3-586">Properties in CLS-compliant types must follow these rules:</span></span>

* <span data-ttu-id="e25a3-587">Bir özelliğin ayarlayıcısı, bir ayarlayıcısı veya her ikisi de olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-587">A property must have a setter, a getter, or both.</span></span> <span data-ttu-id="e25a3-588">Bir derlemede, bunlar ayrı yöntemler olarak görünecekleri anlamına gelen özel yöntemler olarak `get` \_uygulanır (alıcıya özellik *adı* verilir ve ayarlayıcı özellik `set` \_ *adıdır)* derlemenin meta verilerinde işaretlenir. `SpecialName`</span><span class="sxs-lookup"><span data-stu-id="e25a3-588">In an assembly, these are implemented as special methods, which means that they will appear as separate methods (the getter is named `get`\_*propertyname* and the setter is `set`\_*propertyname*) marked as `SpecialName` in the assembly's metadata.</span></span> <span data-ttu-id="e25a3-589">C# derleyicisi özniteliği uygulamaya <xref:System.CLSCompliantAttribute> gerek kalmadan bu kuralı otomatik olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="e25a3-589">The C# compiler enforces this rule automatically without the need to apply the <xref:System.CLSCompliantAttribute> attribute.</span></span>

* <span data-ttu-id="e25a3-590">Bir özelliğin türü, özellik getterinin iade türüdür ve ayarlayıcının son bağımsız değişkenidir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-590">A property's type is the return type of the property getter and the last argument of the setter.</span></span> <span data-ttu-id="e25a3-591">Bu türler CLS uyumlu olmalıdır ve bağımsız değişkenler başvuru ile özelliğe atanamaz (diğer bir şekilde, bunlar yönetilemez işaretçileri).</span><span class="sxs-lookup"><span data-stu-id="e25a3-591">These types must be CLS compliant, and arguments cannot be assigned to the property by reference (that is, they cannot be managed pointers).</span></span>

* <span data-ttu-id="e25a3-592">Bir özelliğin hem getter hem de ayarlayıcısı varsa, her ikisi de sanal, hem statik veya her iki örnek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-592">If a property has both a getter and a setter, they must both be virtual, both static, or both instance.</span></span> <span data-ttu-id="e25a3-593">C# derleyicisi bu kuralı özellik tanımı sözdizimi aracılığıyla otomatik olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="e25a3-593">The C# compiler automatically enforces this rule through property definition syntax.</span></span>

### <a name="events"></a><span data-ttu-id="e25a3-594">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e25a3-594">Events</span></span>

<span data-ttu-id="e25a3-595">Bir olay, adı ve türüne göre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-595">An event is defined by its name and its type.</span></span> <span data-ttu-id="e25a3-596">Olay türü, olayı belirtmek için kullanılan bir temsilcidir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-596">The event type is a delegate that is used to indicate the event.</span></span> <span data-ttu-id="e25a3-597">Örneğin, `DbConnection.StateChange` olay türü. `StateChangeEventHandler`</span><span class="sxs-lookup"><span data-stu-id="e25a3-597">For example, the `DbConnection.StateChange` event is of type `StateChangeEventHandler`.</span></span> <span data-ttu-id="e25a3-598">Olayın kendisine ek olarak, olay adına dayalı adlara sahip üç yöntem etkinliğin `SpecialName` uygulanmasını sağlar ve derlemenin meta verilerinde olduğu gibi işaretlenir:</span><span class="sxs-lookup"><span data-stu-id="e25a3-598">In addition to the event itself, three methods with names based on the event name provide the event's implementation and are marked as `SpecialName` in the assembly's metadata:</span></span>

* <span data-ttu-id="e25a3-599">_ `add`*EventName*adlı bir olay işleyicisi ekleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e25a3-599">A method for adding an event handler, named `add`_*EventName*.</span></span> <span data-ttu-id="e25a3-600">Örneğin, `DbConnection.StateChange` olay için olay abonelik yöntemi `add_StateChange`adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-600">For example, the event subscription method for the `DbConnection.StateChange` event is named `add_StateChange`.</span></span>

* <span data-ttu-id="e25a3-601">_ `remove`*EventName*adlı bir olay işleyicisi kaldırmak için bir yöntem .</span><span class="sxs-lookup"><span data-stu-id="e25a3-601">A method for removing an event handler, named `remove`_*EventName*.</span></span> <span data-ttu-id="e25a3-602">Örneğin, `DbConnection.StateChange` olayın kaldırma yöntemi adlandırılmış. `remove_StateChange`</span><span class="sxs-lookup"><span data-stu-id="e25a3-602">For example, the removal method for the `DbConnection.StateChange` event is named `remove_StateChange`.</span></span>

* <span data-ttu-id="e25a3-603">Olayın oluştuğunu belirten bir yöntem, `raise` \_ *EventName*adlı .</span><span class="sxs-lookup"><span data-stu-id="e25a3-603">A method for indicating that the event has occurred, named `raise`\_*EventName*.</span></span>

> [!NOTE]
> <span data-ttu-id="e25a3-604">Ortak Dil Belirtimi'nin olaylarla ilgili kurallarının çoğu dil derleyicileri tarafından uygulanır ve bileşen geliştiricileri için saydamdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-604">Most of the Common Language Specification's rules regarding events are implemented by language compilers and are transparent to component developers.</span></span>

<span data-ttu-id="e25a3-605">Olayı ekleme, kaldırma ve yükseltme yöntemleri aynı erişilebilirlikte olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-605">The methods for adding, removing, and raising the event must have the same accessibility.</span></span> <span data-ttu-id="e25a3-606">Bunların hepsi statik, örnek veya sanal olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-606">They must also all be static, instance, or virtual.</span></span> <span data-ttu-id="e25a3-607">Olay ekleme ve kaldırma yöntemlerinin, olay temsilcisi türü olan bir parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-607">The methods for adding and removing an event have one parameter whose type is the event delegate type.</span></span> <span data-ttu-id="e25a3-608">Ekleme ve kaldırma yöntemleri nin her ikisi de mevcut olmalı veya her ikisi de bulunmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-608">The add and remove methods must both be present or both be absent.</span></span>

<span data-ttu-id="e25a3-609">Aşağıdaki örnek, iki okuma arasındaki sıcaklık `Temperature` değişimi `TemperatureChanged` bir eşik değerine eşit sayılsa veya aşarsa, olayı yükselten CLS uyumlu bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-609">The following example defines a CLS-compliant class named `Temperature` that raises a `TemperatureChanged` event if the change in temperature between two readings equals or exceeds a threshold value.</span></span> <span data-ttu-id="e25a3-610">Sınıf, `Temperature` olay işleyicilerini seçiçle yürütebilmek için bir `raise_TemperatureChanged` metodu açıkça tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-610">The `Temperature` class explicitly defines a `raise_TemperatureChanged` method so that it can selectively execute event handlers.</span></span>

```csharp
using System;
using System.Collections;
using System.Collections.Generic;

[assembly: CLSCompliant(true)]

public class TemperatureChangedEventArgs : EventArgs
{
   private Decimal originalTemp;
   private Decimal newTemp;
   private DateTimeOffset when;

   public TemperatureChangedEventArgs(Decimal original, Decimal @new, DateTimeOffset time)
   {
      originalTemp = original;
      newTemp = @new;
      when = time;
   }

   public Decimal OldTemperature
   {
      get { return originalTemp; }
   }

   public Decimal CurrentTemperature
   {
      get { return newTemp; }
   }

   public DateTimeOffset Time
   {
      get { return when; }
   }
}

public delegate void TemperatureChanged(Object sender, TemperatureChangedEventArgs e);

public class Temperature
{
   private struct TemperatureInfo
   {
      public Decimal Temperature;
      public DateTimeOffset Recorded;
   }

   public event TemperatureChanged TemperatureChanged;

   private Decimal previous;
   private Decimal current;
   private Decimal tolerance;
   private List<TemperatureInfo> tis = new List<TemperatureInfo>();

   public Temperature(Decimal temperature, Decimal tolerance)
   {
      current = temperature;
      TemperatureInfo ti = new TemperatureInfo();
      ti.Temperature = temperature;
      tis.Add(ti);
      ti.Recorded = DateTimeOffset.UtcNow;
      this.tolerance = tolerance;
   }

   public Decimal CurrentTemperature
   {
      get { return current; }
      set {
         TemperatureInfo ti = new TemperatureInfo();
         ti.Temperature = value;
         ti.Recorded = DateTimeOffset.UtcNow;
         previous = current;
         current = value;
         if (Math.Abs(current - previous) >= tolerance)
            raise_TemperatureChanged(new TemperatureChangedEventArgs(previous, current, ti.Recorded));
      }
   }

   public void raise_TemperatureChanged(TemperatureChangedEventArgs eventArgs)
   {
      if (TemperatureChanged == null)
         return;

      foreach (TemperatureChanged d in TemperatureChanged.GetInvocationList()) {
         if (d.Method.Name.Contains("Duplicate"))
            Console.WriteLine("Duplicate event handler; event handler not executed.");
         else
            d.Invoke(this, eventArgs);
      }
   }
}

public class Example
{
   public Temperature temp;

   public static void Main()
   {
      Example ex = new Example();
   }

   public Example()
   {
      temp = new Temperature(65, 3);
      temp.TemperatureChanged += this.TemperatureNotification;
      RecordTemperatures();
      Example ex = new Example(temp);
      ex.RecordTemperatures();
   }

   public Example(Temperature t)
   {
      temp = t;
      RecordTemperatures();
   }

   public void RecordTemperatures()
   {
      temp.TemperatureChanged += this.DuplicateTemperatureNotification;
      temp.CurrentTemperature = 66;
      temp.CurrentTemperature = 63;
   }

   internal void TemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }

   public void DuplicateTemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }
}
```

```vb
Imports System.Collections
Imports System.Collections.Generic

<Assembly: CLSCompliant(True)>

Public Class TemperatureChangedEventArgs   : Inherits EventArgs
   Private originalTemp As Decimal
   Private newTemp As Decimal
   Private [when] As DateTimeOffset

   Public Sub New(original As Decimal, [new] As Decimal, [time] As DateTimeOffset)
      originalTemp = original
      newTemp = [new]
      [when] = [time]
   End Sub

   Public ReadOnly Property OldTemperature As Decimal
      Get
         Return originalTemp
      End Get
   End Property

   Public ReadOnly Property CurrentTemperature As Decimal
      Get
         Return newTemp
      End Get
   End Property

   Public ReadOnly Property [Time] As DateTimeOffset
      Get
         Return [when]
      End Get
   End Property
End Class

Public Delegate Sub TemperatureChanged(sender As Object, e As TemperatureChangedEventArgs)

Public Class Temperature
   Private Structure TemperatureInfo
      Dim Temperature As Decimal
      Dim Recorded As DateTimeOffset
   End Structure

   Public Event TemperatureChanged As TemperatureChanged

   Private previous As Decimal
   Private current As Decimal
   Private tolerance As Decimal
   Private tis As New List(Of TemperatureInfo)

   Public Sub New(temperature As Decimal, tolerance As Decimal)
      current = temperature
      Dim ti As New TemperatureInfo()
      ti.Temperature = temperature
      ti.Recorded = DateTimeOffset.UtcNow
      tis.Add(ti)
      Me.tolerance = tolerance
   End Sub

   Public Property CurrentTemperature As Decimal
      Get
         Return current
      End Get
      Set
         Dim ti As New TemperatureInfo
         ti.Temperature = value
         ti.Recorded = DateTimeOffset.UtcNow
         previous = current
         current = value
         If Math.Abs(current - previous) >= tolerance Then
            raise_TemperatureChanged(New TemperatureChangedEventArgs(previous, current, ti.Recorded))
         End If
      End Set
   End Property

   Public Sub raise_TemperatureChanged(eventArgs As TemperatureChangedEventArgs)
      If TemperatureChangedEvent Is Nothing Then Exit Sub

      Dim ListenerList() As System.Delegate = TemperatureChangedEvent.GetInvocationList()
      For Each d As TemperatureChanged In TemperatureChangedEvent.GetInvocationList()
         If d.Method.Name.Contains("Duplicate") Then
            Console.WriteLine("Duplicate event handler; event handler not executed.")
         Else
            d.Invoke(Me, eventArgs)
         End If
      Next
   End Sub
End Class

Public Class Example
   Public WithEvents temp As Temperature

   Public Shared Sub Main()
      Dim ex As New Example()
   End Sub

   Public Sub New()
      temp = New Temperature(65, 3)
      RecordTemperatures()
      Dim ex As New Example(temp)
      ex.RecordTemperatures()
   End Sub

   Public Sub New(t As Temperature)
      temp = t
      RecordTemperatures()
   End Sub

   Public Sub RecordTemperatures()
      temp.CurrentTemperature = 66
      temp.CurrentTemperature = 63

   End Sub

   Friend Shared Sub TemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub

   Friend Shared Sub DuplicateTemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub
End Class
```

### <a name="overloads"></a><span data-ttu-id="e25a3-611">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="e25a3-611">Overloads</span></span>

<span data-ttu-id="e25a3-612">Ortak Dil Belirtimi, aşırı yüklü üyelere aşağıdaki gereksinimleri uygular:</span><span class="sxs-lookup"><span data-stu-id="e25a3-612">The Common Language Specification imposes the following requirements on overloaded members:</span></span>

* <span data-ttu-id="e25a3-613">Üyeler, parametrelerin sayısına ve herhangi bir parametrenin türüne göre aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-613">Members can be overloaded based on the number of parameters and the type of any parameter.</span></span> <span data-ttu-id="e25a3-614">Arama kuralı, iade türü, yönteme veya parametresine uygulanan özel değiştiriciler ve parametrelerin değer veya referans tarafından geçirilip geçirilemediği, aşırı yükler arasında ayrım yaparken dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-614">Calling convention, return type, custom modifiers applied to the method or its parameter, and whether parameters are passed by value or by reference are not considered when differentiating between overloads.</span></span> <span data-ttu-id="e25a3-615">Örneğin, [Adlandırma kuralları](#naming-conventions) bölümünde ki bir kapsamda adların benzersiz olması gereksiniminin kodunu görün.</span><span class="sxs-lookup"><span data-stu-id="e25a3-615">For an example, see the code for the requirement that names must be unique within a scope in the [Naming conventions](#naming-conventions) section.</span></span>

* <span data-ttu-id="e25a3-616">Yalnızca özellikler ve yöntemler aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-616">Only properties and methods can be overloaded.</span></span> <span data-ttu-id="e25a3-617">Alanlar ve olaylar aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="e25a3-617">Fields and events cannot be overloaded.</span></span>

* <span data-ttu-id="e25a3-618">Genel yöntemler, genel parametrelerinsayısına bağlı olarak aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-618">Generic methods can be overloaded based on the number of their generic parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="e25a3-619">Ve `op_Explicit` `op_Implicit` işleçler, iade değerinin aşırı yük çözümü için yöntem imzasının bir parçası olarak kabul edilmeme kuralının istisnalarıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-619">The `op_Explicit` and `op_Implicit` operators are exceptions to the rule that return value is not considered part of a method signature for overload resolution.</span></span> <span data-ttu-id="e25a3-620">Bu iki işleç hem parametrelerine hem de getiri değerine göre aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-620">These two operators can be overloaded based on both their parameters and their return value.</span></span>

### <a name="exceptions"></a><span data-ttu-id="e25a3-621">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="e25a3-621">Exceptions</span></span>

<span data-ttu-id="e25a3-622">Özel durum nesneleri [System.Exception'dan](xref:System.Exception) veya türetilen `System.Exception`başka bir türden türemelidir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-622">Exception objects must derive from [System.Exception](xref:System.Exception) or from another type derived from `System.Exception`.</span></span> <span data-ttu-id="e25a3-623">Aşağıdaki örnek, özel durum işleme için özel `ErrorClass` bir sınıf kullanıldığında ortaya çıkan derleyici hatasını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-623">The following example illustrates the compiler error that results when a custom class named `ErrorClass` is used for exception handling.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
// Compilation produces a compiler error like the following:
//    Exceptions1.cs(26,16): error CS0155: The type caught or thrown must be derived from
//            System.Exception
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
' Compilation produces a compiler error like the following:
'    Exceptions1.vb(27) : error BC30665: 'Throw' operand must derive from 'System.Exception'.
'
'             Throw BadIndex
'             ~~~~~~~~~~~~~~
```

<span data-ttu-id="e25a3-624">Bu hatayı düzeltmek `ErrorClass` için sınıfın `System.Exception`.'den devralması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-624">To correct this error, the `ErrorClass` class must inherit from `System.Exception`.</span></span> <span data-ttu-id="e25a3-625">Ayrıca, İleti özelliği geçersiz kılınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-625">In addition, the Message property must be overridden.</span></span> <span data-ttu-id="e25a3-626">Aşağıdaki örnek, CLS uyumlu `ErrorClass` bir sınıf tanımlamak için bu hataları düzeltir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-626">The following example corrects these errors to define an `ErrorClass` class that is CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass : Exception
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public override string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass : Inherits Exception
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public Overrides ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
```

### <a name="attributes"></a><span data-ttu-id="e25a3-627">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e25a3-627">Attributes</span></span>

<span data-ttu-id="e25a3-628">In.NET Framework derlemeleri, özel öznitelikleri özel öznitelikleri depolamak ve derlemeler, türler, üyeler ve yöntem parametreleri gibi programlama nesneleri hakkında meta veri almak için genişletilebilir bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-628">In.NET Framework assemblies, custom attributes provide an extensible mechanism for storing custom attributes and retrieving metadata about programming objects, such as assemblies, types, members, and method parameters.</span></span> <span data-ttu-id="e25a3-629">Özel öznitelikler [System.Attribute'ten](xref:System.Attribute) veya `System.Attribute`türetilen bir türden türemelidir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-629">Custom attributes must derive from [System.Attribute](xref:System.Attribute) or from a type derived from `System.Attribute`.</span></span>

<span data-ttu-id="e25a3-630">Aşağıdaki örnek bu kuralı ihlal eder.</span><span class="sxs-lookup"><span data-stu-id="e25a3-630">The following example violates this rule.</span></span> <span data-ttu-id="e25a3-631">Bu türetilmiştir olmayan bir `NumericAttribute` sınıf `System.Attribute`tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-631">It defines a `NumericAttribute` class that does not derive from `System.Attribute`.</span></span> <span data-ttu-id="e25a3-632">Derleyici hatasının yalnızca CLS uyumlu olmayan öznitelik uygulandığında, sınıf tanımlandığında değil, sonucu olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e25a3-632">Note that a compiler error results only when the non-CLS-compliant attribute is applied, not when the class is defined.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

[AttributeUsageAttribute(AttributeTargets.Class | AttributeTargets.Struct)]
public class NumericAttribute
{
   private bool _isNumeric;

   public NumericAttribute(bool isNumeric)
   {
      _isNumeric = isNumeric;
   }

   public bool IsNumeric
   {
      get { return _isNumeric; }
   }
}

[Numeric(true)] public struct UDouble
{
   double Value;
}
// Compilation produces a compiler error like the following:
//    Attribute1.cs(22,2): error CS0616: 'NumericAttribute' is not an attribute class
//    Attribute1.cs(7,14): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

<AttributeUsageAttribute(AttributeTargets.Class Or AttributeTargets.Struct)> _
Public Class NumericAttribute
   Private _isNumeric As Boolean

   Public Sub New(isNumeric As Boolean)
      _isNumeric = isNumeric
   End Sub

   Public ReadOnly Property IsNumeric As Boolean
      Get
         Return _isNumeric
      End Get
   End Property
End Class

<Numeric(True)> Public Structure UDouble
   Dim Value As Double
End Structure
' Compilation produces a compiler error like the following:
'    error BC31504: 'NumericAttribute' cannot be used as an attribute because it
'    does not inherit from 'System.Attribute'.
'
'    <Numeric(True)> Public Structure UDouble
'     ~~~~~~~~~~~~~
```

<span data-ttu-id="e25a3-633">CLS uyumlu bir özniteliğin oluşturucu suveya özellikleri yalnızca aşağıdaki türleri ortaya çıkarabilir:</span><span class="sxs-lookup"><span data-stu-id="e25a3-633">The constructor or the properties of a CLS-compliant attribute can expose only the following types:</span></span>

* [<span data-ttu-id="e25a3-634">Boole</span><span class="sxs-lookup"><span data-stu-id="e25a3-634">Boolean</span></span>](xref:System.Boolean)

* [<span data-ttu-id="e25a3-635">Bayt</span><span class="sxs-lookup"><span data-stu-id="e25a3-635">Byte</span></span>](xref:System.Byte)

* [<span data-ttu-id="e25a3-636">Char</span><span class="sxs-lookup"><span data-stu-id="e25a3-636">Char</span></span>](xref:System.Char)

* [<span data-ttu-id="e25a3-637">Çift</span><span class="sxs-lookup"><span data-stu-id="e25a3-637">Double</span></span>](xref:System.Double)

* [<span data-ttu-id="e25a3-638">Int16</span><span class="sxs-lookup"><span data-stu-id="e25a3-638">Int16</span></span>](xref:System.Int16)

* [<span data-ttu-id="e25a3-639">Int32</span><span class="sxs-lookup"><span data-stu-id="e25a3-639">Int32</span></span>](xref:System.Int32)

* [<span data-ttu-id="e25a3-640">Int64</span><span class="sxs-lookup"><span data-stu-id="e25a3-640">Int64</span></span>](xref:System.Int64)

* [<span data-ttu-id="e25a3-641">Tek</span><span class="sxs-lookup"><span data-stu-id="e25a3-641">Single</span></span>](xref:System.Single)

* [<span data-ttu-id="e25a3-642">Dize</span><span class="sxs-lookup"><span data-stu-id="e25a3-642">String</span></span>](xref:System.String)

* [<span data-ttu-id="e25a3-643">Tür</span><span class="sxs-lookup"><span data-stu-id="e25a3-643">Type</span></span>](xref:System.Type)

* <span data-ttu-id="e25a3-644">Altta yatan `Byte`türü , , `Int16` `Int32`, veya `Int64`.</span><span class="sxs-lookup"><span data-stu-id="e25a3-644">Any enumeration type whose underlying type is `Byte`, `Int16`, `Int32`, or `Int64`.</span></span>

<span data-ttu-id="e25a3-645">Aşağıdaki örnek, `DescriptionAttribute` [Atnitelik'ten](xref:System.Attribute)türeyen bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-645">The following example defines a `DescriptionAttribute` class that derives from [Attribute](xref:System.Attribute).</span></span> <span data-ttu-id="e25a3-646">Sınıf oluşturucu türü bir parametre `Descriptor`vardır, bu nedenle sınıf CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-646">The class constructor has a parameter of type `Descriptor`, so the class is not CLS-compliant.</span></span> <span data-ttu-id="e25a3-647">C# derleyicisinin bir uyarı yayan ancak başarılı bir şekilde derlediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e25a3-647">Note that the C# compiler emits a warning but compiles successfully.</span></span>

```csharp
using System;

[assembly:CLSCompliantAttribute(true)]

public enum DescriptorType { type, member };

public class Descriptor
{
   public DescriptorType Type;
   public String Description;
}

[AttributeUsage(AttributeTargets.All)]
public class DescriptionAttribute : Attribute
{
   private Descriptor desc;

   public DescriptionAttribute(Descriptor d)
   {
      desc = d;
   }

   public Descriptor Descriptor
   { get { return desc; } }
}
// Attempting to compile the example displays output like the following:
//       warning CS3015: 'DescriptionAttribute' has no accessible
//               constructors which use only CLS-compliant types
```

```vb
<Assembly:CLSCompliantAttribute(True)>

Public Enum DescriptorType As Integer
   Type = 0
   Member = 1
End Enum

Public Class Descriptor
   Public Type As DescriptorType
   Public Description As String
End Class

<AttributeUsage(AttributeTargets.All)> _
Public Class DescriptionAttribute : Inherits Attribute
   Private desc As Descriptor

   Public Sub New(d As Descriptor)
      desc = d
   End Sub

   Public ReadOnly Property Descriptor As Descriptor
      Get
         Return desc
      End Get
   End Property
End Class
```

## <a name="the-clscompliantattribute-attribute"></a><span data-ttu-id="e25a3-648">CLSCompliantAttribute özniteliği</span><span class="sxs-lookup"><span data-stu-id="e25a3-648">The CLSCompliantAttribute attribute</span></span>

<span data-ttu-id="e25a3-649">[CLSCompliantAttribute özniteliği,](xref:System.CLSCompliantAttribute) bir program öğesinin Ortak Dil Belirtimine uyup uymadığını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-649">The [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is used to indicate whether a program element complies with the Common Language Specification.</span></span> <span data-ttu-id="e25a3-650">Oluşturucu, `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` program öğesinin CLS uyumlu olup olmadığını gösteren tek bir gerekli parametre, *isCompliant*içerir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-650">The `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` constructor includes a single required parameter, *isCompliant*, that indicates whether the program element is CLS-compliant.</span></span>

<span data-ttu-id="e25a3-651">Derleme zamanında derleyici, CLS uyumlu olduğu tahmin edilen uyumlu olmayan öğeleri algılar ve bir uyarı yatar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-651">At compile time, the compiler detects non-compliant elements that are presumed to be CLS-compliant and emits a warning.</span></span> <span data-ttu-id="e25a3-652">Derleyici, açıkça uyumsuz olduğu bildirilen türler veya üyeler için uyarı lar yayan değildir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-652">The compiler does not emit warnings for types or members that are explicitly declared to be non-compliant.</span></span>

<span data-ttu-id="e25a3-653">Bileşen geliştiriciler özniteliği `CLSCompliantAttribute` iki şekilde kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="e25a3-653">Component developers can use the `CLSCompliantAttribute` attribute in two ways:</span></span>

* <span data-ttu-id="e25a3-654">Ortak arabirimin CLS uyumlu bir bileşen ve CLS uyumlu olmayan bölümleri tarafından maruz kalan bölümlerini tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="e25a3-654">To define the parts of the public interface exposed by a component that are CLS-compliant and the parts that are not CLS-compliant.</span></span> <span data-ttu-id="e25a3-655">Özellik, belirli program öğelerini CLS uyumlu olarak işaretlemek için kullanıldığında, kullanımı bu öğelerin .NET Framework'ünü hedefleyen tüm dil ve araçlardan erişilebilir olduğunu garanti eder.</span><span class="sxs-lookup"><span data-stu-id="e25a3-655">When the attribute is used to mark particular program elements as CLS-compliant, its use guarantees that those elements are accessible from all languages and tools that target the .NET Framework.</span></span>

* <span data-ttu-id="e25a3-656">Bileşen kitaplığın ortak arabiriminin yalnızca CLS uyumlu program öğelerini ortaya çıkarmasını sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="e25a3-656">To ensure that the component library's public interface exposes only program elements that are CLS-compliant.</span></span> <span data-ttu-id="e25a3-657">Öğeler CLS uyumlu değilse, derleyiciler genellikle bir uyarı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-657">If elements are not CLS-compliant, compilers will generally issue a warning.</span></span>

> [!WARNING]
> <span data-ttu-id="e25a3-658">Bazı durumlarda, dil derleyicileri özniteliğin `CLSCompliantAttribute` kullanılıp kullanılmadığına bakılmaksızın CLS uyumlu kuralları uygular.</span><span class="sxs-lookup"><span data-stu-id="e25a3-658">In some cases, language compilers enforce CLS-compliant rules regardless of whether the `CLSCompliantAttribute` attribute is used.</span></span> <span data-ttu-id="e25a3-659">Örneğin, bir arabirimde bir `*static` üyetanımlamak bir CLS kuralını ihlal eder.</span><span class="sxs-lookup"><span data-stu-id="e25a3-659">For example, defining a `*static` member in an interface violates a CLS rule.</span></span> <span data-ttu-id="e25a3-660">Ancak, bir arabirimde bir `*static` üye tanımlarsanız, C# derleyicisi bir hata iletisi görüntüler ve uygulamayı derlemede başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e25a3-660">However, if you define a `*static` member in an interface, the C# compiler displays an error message and fails to compile the app.</span></span>

<span data-ttu-id="e25a3-661">Öznitelik, `CLSCompliantAttribute` değeri . [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) `AttributeTargets.All`</span><span class="sxs-lookup"><span data-stu-id="e25a3-661">The `CLSCompliantAttribute` attribute is marked with an [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) attribute that has a value of `AttributeTargets.All`.</span></span> <span data-ttu-id="e25a3-662">Bu değer, özniteliği `CLSCompliantAttribute` derlemeler, modüller, türler (sınıflar, yapılar, arabirimler ve temsilciler), tür üyeleri (oluşturucular, yöntemler, özellikler, alanlar ve olaylar), parametreler, genel parametreler ve iade değerleri dahil olmak üzere herhangi bir program öğesine uygulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-662">This value allows you to apply the `CLSCompliantAttribute` attribute to any program element, including assemblies, modules, types (classes, structures, enumerations, interfaces, and delegates), type members (constructors, methods, properties, fields, and events), parameters, generic parameters, and return values.</span></span> <span data-ttu-id="e25a3-663">Ancak, uygulamada, özniteliği yalnızca derlemelere, türlere ve tür üyelerine uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-663">However, in practice, you should apply the attribute only to assemblies, types, and type members.</span></span> <span data-ttu-id="e25a3-664">Aksi takdirde, derleyiciler özniteliği yoklar ve kitaplığınızın ortak arabiriminde uyumlu olmayan bir parametre, genel parametre veya iade değeriyle karşılaştıklarında derleyici uyarıları oluşturmaya devam ederler.</span><span class="sxs-lookup"><span data-stu-id="e25a3-664">Otherwise, compilers ignore the attribute and continue to generate compiler warnings whenever they encounter a non-compliant parameter, generic parameter, or return value in your library's public interface.</span></span>

<span data-ttu-id="e25a3-665">Özniteliğin `CLSCompliantAttribute` değeri, içerdiği program öğeleri tarafından devralınR.</span><span class="sxs-lookup"><span data-stu-id="e25a3-665">The value of the `CLSCompliantAttribute` attribute is inherited by contained program elements.</span></span> <span data-ttu-id="e25a3-666">Örneğin, bir derleme CLS uyumlu olarak işaretlenmişse, türleri de CLS uyumludur.</span><span class="sxs-lookup"><span data-stu-id="e25a3-666">For example, if an assembly is marked as CLS-compliant, its types are also CLS-compliant.</span></span> <span data-ttu-id="e25a3-667">Bir tür CLS uyumlu olarak işaretlenmişse, iç içe olan türleri ve üyeleri de CLS uyumludur.</span><span class="sxs-lookup"><span data-stu-id="e25a3-667">If a type is marked as CLS-compliant, its nested types and members are also CLS-compliant.</span></span>

<span data-ttu-id="e25a3-668">Özniteliği içerdiği bir program öğesine uygulayarak `CLSCompliantAttribute` devralınan uyumluluğu açıkça geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-668">You can explicitly override the inherited compliance by applying the `CLSCompliantAttribute` attribute to a contained program element.</span></span> <span data-ttu-id="e25a3-669">Örneğin, uyumlu olmayan `CLSCompliantAttribute` bir derlemede uyumlu olmayan `false` bir türü tanımlamak için *isCompliant* değerine sahip özniteliği kullanabilir *isCompliant* ve uyumlu `true` olmayan bir derlemede uyumlu bir türü tanımlamak için uyumlu bir değere sahip özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-669">For example, you can use the `CLSCompliantAttribute` attribute with an *isCompliant* value of `false` to define a non-compliant type in a compliant assembly, and you can use the attribute with an *isCompliant* value of `true` to define a compliant type in a non-compliant assembly.</span></span> <span data-ttu-id="e25a3-670">Uyumlu olmayan üyeleri uyumlu bir türde de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-670">You can also define non-compliant members in a compliant type.</span></span> <span data-ttu-id="e25a3-671">Ancak, uyumlu olmayan bir tür uyumlu üyeleri olamaz, bu nedenle uyumlu olmayan `true` bir tür devralma geçersiz kılmak için bir *isCompliant* değeri ile özniteliği kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e25a3-671">However, a non-compliant type cannot have compliant members, so you cannot use the attribute with an *isCompliant* value of `true` to override inheritance from a non-compliant type.</span></span>

<span data-ttu-id="e25a3-672">Bileşenler geliştirirken, derlemenizin, `CLSCompliantAttribute` türlerinin ve üyelerinin CLS uyumlu olup olmadığını belirtmek için özniteliği her zaman kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-672">When you are developing components, you should always use the `CLSCompliantAttribute` attribute to indicate whether your assembly, its types, and its members are CLS-compliant.</span></span>

<span data-ttu-id="e25a3-673">CLS uyumlu bileşenler oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="e25a3-673">To create CLS-compliant components:</span></span>

1. <span data-ttu-id="e25a3-674">Montajını `CLSCompliantAttribute` CLS uyumlu olarak işaretlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e25a3-674">Use the `CLSCompliantAttribute` to mark you assembly as CLS-compliant.</span></span>

2. <span data-ttu-id="e25a3-675">Derlemede, CLS uyumlu olmayan tüm genel olarak açıklanmış türleri uyumlu olmayan olarak işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="e25a3-675">Mark any publicly exposed types in the assembly that are not CLS-compliant as non-compliant.</span></span>

3. <span data-ttu-id="e25a3-676">CLS uyumlu türdeki herkese açık üyeleri uyumlu olmayan olarak işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="e25a3-676">Mark any publicly exposed members in CLS-compliant types as non-compliant.</span></span>

4. <span data-ttu-id="e25a3-677">CLS uyumlu olmayan üyeler için CLS uyumlu bir alternatif sağlayın.</span><span class="sxs-lookup"><span data-stu-id="e25a3-677">Provide a CLS-compliant alternative for non-CLS-compliant members.</span></span>

<span data-ttu-id="e25a3-678">Tüm uyumlu olmayan türlerinizi ve üyelerinizi başarıyla işaretlediyseniz, derleyiciniz herhangi bir uyumsuzluk uyarısı yaslanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-678">If you've successfully marked all your non-compliant types and members, your compiler should not emit any non-compliance warnings.</span></span> <span data-ttu-id="e25a3-679">Ancak, hangi üyelerin CLS uyumlu olmadığını belirtmeli ve ürün belgelerinizde CLS uyumlu alternatiflerini listelemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-679">However, you should indicate which members are not CLS-compliant and list their CLS-compliant alternatives in your product documentation.</span></span>

<span data-ttu-id="e25a3-680">Aşağıdaki örnek, `CLSCompliantAttribute` CLS uyumlu olmayan iki üyesi olan bir `CharacterUtilities`CLS uyumlu derleme ve bir tür tanımlamak için özniteliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-680">The following example uses the `CLSCompliantAttribute` attribute to define a CLS-compliant assembly and a type, `CharacterUtilities`, that has two non-CLS-compliant members.</span></span> <span data-ttu-id="e25a3-681">Her iki üye de `CLSCompliant(false)` öznitelik ile etiketlenmiş olduğundan, derleyici hiçbir uyarı üretir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-681">Because both members are tagged with the `CLSCompliant(false)` attribute, the compiler produces no warnings.</span></span> <span data-ttu-id="e25a3-682">Sınıf ayrıca her iki yöntem için cls uyumlu bir alternatif sağlar.</span><span class="sxs-lookup"><span data-stu-id="e25a3-682">The class also provides a CLS-compliant alternative for both methods.</span></span> <span data-ttu-id="e25a3-683">Normalde, CLS uyumlu alternatifler sağlamak için `ToUTF16` yönteme iki aşırı yükleme ekleriz.</span><span class="sxs-lookup"><span data-stu-id="e25a3-683">Ordinarily, we would just add two overloads to the `ToUTF16` method to provide CLS-compliant alternatives.</span></span> <span data-ttu-id="e25a3-684">Ancak, yöntemler iade değerine göre aşırı yüklenemediğinden, CLS uyumlu yöntemlerin adları uyumlu olmayan yöntemlerin adlarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-684">However, because methods cannot be overloaded based on return value, the names of the CLS-compliant methods are different from the names of the non-compliant methods.</span></span>

```csharp
using System;
using System.Text;

[assembly:CLSCompliant(true)]

public class CharacterUtilities
{
   [CLSCompliant(false)] public static ushort ToUTF16(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return Convert.ToUInt16(s[0]);
   }

   [CLSCompliant(false)] public static ushort ToUTF16(Char ch)
   {
      return Convert.ToUInt16(ch);
   }

   // CLS-compliant alternative for ToUTF16(String).
   public static int ToUTF16CodeUnit(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return (int) Convert.ToUInt16(s[0]);
   }

   // CLS-compliant alternative for ToUTF16(Char).
   public static int ToUTF16CodeUnit(Char ch)
   {
      return Convert.ToInt32(ch);
   }

   public bool HasMultipleRepresentations(String s)
   {
      String s1 = s.Normalize(NormalizationForm.FormC);
      return s.Equals(s1);
   }

   public int GetUnicodeCodePoint(Char ch)
   {
      if (Char.IsSurrogate(ch))
         throw new ArgumentException("ch cannot be a high or low surrogate.");

      return Char.ConvertToUtf32(ch.ToString(), 0);
   }

   public int GetUnicodeCodePoint(Char[] chars)
   {
      if (chars.Length > 2)
         throw new ArgumentException("The array has too many characters.");

      if (chars.Length == 2) {
         if (! Char.IsSurrogatePair(chars[0], chars[1]))
            throw new ArgumentException("The array must contain a low and a high surrogate.");
         else
            return Char.ConvertToUtf32(chars[0], chars[1]);
      }
      else {
         return Char.ConvertToUtf32(chars.ToString(), 0);
      }
   }
}
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class CharacterUtilities
   <CLSCompliant(False)> Public Shared Function ToUTF16(s As String) As UShort
      s = s.Normalize(NormalizationForm.FormC)
      Return Convert.ToUInt16(s(0))
   End Function

   <CLSCompliant(False)> Public Shared Function ToUTF16(ch As Char) As UShort
      Return Convert.ToUInt16(ch)
   End Function

   ' CLS-compliant alternative for ToUTF16(String).
   Public Shared Function ToUTF16CodeUnit(s As String) As Integer
      s = s.Normalize(NormalizationForm.FormC)
      Return CInt(Convert.ToInt16(s(0)))
   End Function

   ' CLS-compliant alternative for ToUTF16(Char).
   Public Shared Function ToUTF16CodeUnit(ch As Char) As Integer
      Return Convert.ToInt32(ch)
   End Function

   Public Function HasMultipleRepresentations(s As String) As Boolean
      Dim s1 As String = s.Normalize(NormalizationForm.FormC)
      Return s.Equals(s1)
   End Function

   Public Function GetUnicodeCodePoint(ch As Char) As Integer
      If Char.IsSurrogate(ch) Then
         Throw New ArgumentException("ch cannot be a high or low surrogate.")
      End If
      Return Char.ConvertToUtf32(ch.ToString(), 0)
   End Function

   Public Function GetUnicodeCodePoint(chars() As Char) As Integer
      If chars.Length > 2 Then
         Throw New ArgumentException("The array has too many characters.")
      End If
      If chars.Length = 2 Then
         If Not Char.IsSurrogatePair(chars(0), chars(1)) Then
            Throw New ArgumentException("The array must contain a low and a high surrogate.")
         Else
            Return Char.ConvertToUtf32(chars(0), chars(1))
         End If
      Else
         Return Char.ConvertToUtf32(chars.ToString(), 0)
      End If
   End Function
End Class
```

<span data-ttu-id="e25a3-685">Kitaplık yerine bir uygulama geliştiriyorsanız (diğer bir deyişle, diğer uygulama geliştiricileri tarafından tüketilebilen türleri veya üyeleri ifşa etmiyorsanız), uygulamanızın tükettiği program öğelerinin CLS uyumluluğu yalnızca diliniz bunları desteklemiyorsa ilgi nizi çekebilir .</span><span class="sxs-lookup"><span data-stu-id="e25a3-685">If you are developing an app rather than a library (that is, if you aren't exposing types or members that can be consumed by other app developers), the CLS compliance of the program elements that your app consumes are of interest only if your language does not support them.</span></span> <span data-ttu-id="e25a3-686">Bu durumda, CLS uyumlu olmayan bir öğekullanmaya çalıştığınızda dil derleyiciniz bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e25a3-686">In that case, your language compiler will generate an error when you try to use a non-CLS-compliant element.</span></span>

## <a name="cross-language-interoperability"></a><span data-ttu-id="e25a3-687">Diller Arası Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="e25a3-687">Cross-Language Interoperability</span></span>

<span data-ttu-id="e25a3-688">Dil bağımsızlığının birkaç olası anlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-688">Language independence has a number of possible meanings.</span></span> <span data-ttu-id="e25a3-689">Bir anlam, başka bir dilde yazılmış bir uygulamadan bir dilde yazılmış türleri sorunsuz bir şekilde tüketmeiçerir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-689">One meaning involves seamlessly consuming types written in one language from an app written in another language.</span></span> <span data-ttu-id="e25a3-690">Bu makalenin konusu olan ikinci anlamı ise, birden çok dilde yazılmış kodu tek bir .NET Framework derlemesi olarak birleştirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-690">A second meaning, which is the focus of this article, involves combining code written in multiple languages into a single .NET Framework assembly.</span></span>

<span data-ttu-id="e25a3-691">Aşağıdaki örnekte, Iki sınıf içeren Utilities.dll adlı bir sınıf kitaplığı `NumericLib` oluşturarak diller arası birlikte çalışabilirlik ve `StringLib`.</span><span class="sxs-lookup"><span data-stu-id="e25a3-691">The following example illustrates cross-language interoperability by creating a class library named Utilities.dll that includes two classes, `NumericLib` and `StringLib`.</span></span> <span data-ttu-id="e25a3-692">Sınıf `NumericLib` C# ile yazılır ve `StringLib` sınıf Visual Basic ile yazılır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-692">The `NumericLib` class is written in C#, and the `StringLib` class is written in Visual Basic.</span></span> <span data-ttu-id="e25a3-693">Burada, sınıfında `StringUtil.vb` `ToTitleCase` `StringLib` tek bir üye içeren kaynak kodu vebu kod vardır.</span><span class="sxs-lookup"><span data-stu-id="e25a3-693">Here's the source code for `StringUtil.vb`, which includes a single member, `ToTitleCase`, in its `StringLib` class.</span></span>

```vb
Imports System.Collections.Generic
Imports System.Runtime.CompilerServices

Public Module StringLib
   Private exclusions As List(Of String)

   Sub New()
      Dim words() As String = { "a", "an", "and", "of", "the" }
      exclusions = New List(Of String)
      exclusions.AddRange(words)
   End Sub

   <Extension()> _
   Public Function ToTitleCase(title As String) As String
      Dim words() As String = title.Split()
      Dim result As String = String.Empty

      For ctr As Integer = 0 To words.Length - 1
         Dim word As String = words(ctr)
         If ctr = 0 OrElse Not exclusions.Contains(word.ToLower()) Then
            result += word.Substring(0, 1).ToUpper() + _
                      word.Substring(1).ToLower()
         Else
            result += word.ToLower()
         End If
         If ctr <= words.Length - 1 Then
            result += " "
         End If
      Next
      Return result
   End Function
End Module
```

<span data-ttu-id="e25a3-694">Aşağıda `NumericLib` ve `IsEven` olmak üzere iki üyesi olan bir `NearZero` sınıfını tanımlayan NumberUtil.cs için kaynak kodu verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-694">Here's the source code for NumberUtil.cs, which defines a `NumericLib` class that has two members, `IsEven` and `NearZero`.</span></span>

```csharp
using System;

public static class NumericLib
{
   public static bool IsEven(this IConvertible number)
   {
      if (number is Byte ||
          number is SByte ||
          number is Int16 ||
          number is UInt16 ||
          number is Int32 ||
          number is UInt32 ||
          number is Int64)
         return ((long) number) % 2 == 0;
      else if (number is UInt64)
         return ((ulong) number) %2 == 0;
      else
         throw new NotSupportedException("IsEven called for a non-integer value.");
   }

   public static bool NearZero(double number)
   {
      return number < .00001;
   }
}
```

<span data-ttu-id="e25a3-695">İki sınıfı tek bir derlemede paketlemek için bunları modüller halinde derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e25a3-695">To package the two classes in a single assembly, you must compile them into modules.</span></span> <span data-ttu-id="e25a3-696">Visual Basic kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="e25a3-696">To compile the Visual Basic source code file into a module, use this command:</span></span>

```console
vbc /t:module StringUtil.vb
```

<span data-ttu-id="e25a3-697">C# kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="e25a3-697">To compile the C# source code file into a module, use this command:</span></span>

```console
csc /t:module NumberUtil.cs
```

<span data-ttu-id="e25a3-698">Daha sonra iki modülü derlemek için Bağlantı aracını (Link.exe) kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="e25a3-698">You then use the Link tool (Link.exe) to compile the two modules into an assembly:</span></span>

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

<span data-ttu-id="e25a3-699">Aşağıdaki örnek daha `NumericLib.NearZero` sonra `StringLib.ToTitleCase` çağırır ve yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="e25a3-699">The following example then calls the `NumericLib.NearZero` and `StringLib.ToTitleCase` methods.</span></span> <span data-ttu-id="e25a3-700">Hem Visual Basic kodunun hem de C# kodunun her iki sınıftaki yöntemlere erişebildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e25a3-700">Note that both the Visual Basic code and the C# code are able to access the methods in both classes.</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      Double dbl = 0.0 - Double.Epsilon;
      Console.WriteLine(NumericLib.NearZero(dbl));

      string s = "war and peace";
      Console.WriteLine(s.ToTitleCase());
   }
}
// The example displays the following output:
//       True
//       War and Peace
```

```vb
Module Example
   Public Sub Main()
      Dim dbl As Double = 0.0 - Double.Epsilon
      Console.WriteLine(NumericLib.NearZero(dbl))

      Dim s As String = "war and peace"
      Console.WriteLine(s.ToTitleCase())
   End Sub
End Module
' The example displays the following output:
'       True
'       War and Peace
```

<span data-ttu-id="e25a3-701">Visual Basic kodunu derlemek için bu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="e25a3-701">To compile the Visual Basic code, use this command:</span></span>

```console
vbc example.vb /r:UtilityLib.dll
```

<span data-ttu-id="e25a3-702">C# ile derlemek için derleyicinin adını vbc'den csc'ye değiştirin ve dosya uzantısını .vb.'den .cs'ye değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e25a3-702">To compile with C#, change the name of the compiler from vbc to csc, and change the file extension from .vb to .cs:</span></span>

```console
csc example.cs /r:UtilityLib.dll
```
