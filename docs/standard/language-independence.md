---
title: Dil bağımsızlığı ve dilden bağımsız bileşenler
description: '.NET, C#, C + gibi birçok desteklenen dilde birinde nasıl geliştirebileceğinizi öğrenin +/ CLI, F #, IronPython, VB, Visual COBOL ve PowerShell.'
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: 2e54f49f111c545a329a64ede400dc1354020f43
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579515"
---
# <a name="language-independence-and-language-independent-components"></a><span data-ttu-id="d51c0-103">Dil bağımsızlığı ve dilden bağımsız bileşenler</span><span class="sxs-lookup"><span data-stu-id="d51c0-103">Language independence and language-independent components</span></span>

<span data-ttu-id="d51c0-104">.NET bağımsız dilidir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-104">.NET is language independent.</span></span> <span data-ttu-id="d51c0-105">Bu, geliştirici olarak size C#, F # ve Visual Basic gibi .NET uygulamalarında hedef birçok dilde birinde geliştirebilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-105">This means that, as a developer, you can develop in one of the many languages that target .NET implementations, such as C#, F#, and Visual Basic.</span></span> <span data-ttu-id="d51c0-106">Türleri ve sınıf kitaplıkları için .NET uygulamaları, bunlar ilk olarak yazılmış dili bilmenize gerek kalmadan ve özgün dil kuralları birini izleyin gerek kalmadan geliştirilen üyeleri erişebilir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-106">You can access the types and members of class libraries developed for .NET implementations without having to know the language in which they were originally written and without having to follow any of the original language's conventions.</span></span> <span data-ttu-id="d51c0-107">Bileşen geliştiriciyseniz bileşeniniz dili bağımsız olarak herhangi bir .NET uygulama tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-107">If you are a component developer, your component can be accessed by any .NET app regardless of its language.</span></span>

> [!NOTE]
> <span data-ttu-id="d51c0-108">Bu makalede bu ilk kısmı dilden bağımsız bileşenler - diğer bir deyişle, herhangi bir dilde yazılan uygulamaları tarafından kullanılabilecek bileşenler oluşturma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-108">This first part of this article discusses creating language-independent components - that is, components that can be consumed by apps that are written in any language.</span></span> <span data-ttu-id="d51c0-109">Çeşitli dillerde yazılmış kaynak koddan tek bir bileşen ya uygulaması oluşturabilirsiniz; bkz: [diller arası birlikte çalışabilirlik](#cross-language-interoperability) ikinci bölümü, bu makalenin.</span><span class="sxs-lookup"><span data-stu-id="d51c0-109">You can also create a single component or app from source code written in multiple languages; see [Cross-Language Interoperability](#cross-language-interoperability) in the second part of this article.</span></span> 

<span data-ttu-id="d51c0-110">Tam olarak herhangi bir dilde yazılmış diğer nesnelerle etkileşim kurmak için nesneleri, tüm diller için ortak olan özellikleri arayanlara kullanıma gerekir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-110">To fully interact with other objects written in any language, objects must expose to callers only those features that are common to all languages.</span></span> <span data-ttu-id="d51c0-111">Bu ortak bir özellikler kümesi ortak dil belirtimi (CLS tarafından), hangi oluşturulmuş derlemeler için geçerli bir kurallar kümesidir tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-111">This common set of features is defined by the Common Language Specification (CLS), which is a set of rules that apply to generated assemblies.</span></span> <span data-ttu-id="d51c0-112">Ortak dil belirtimi bölüm ı yan tümceleri 7 11 /'ile tanımlanan [ECMA-335 standart: ortak dil altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="d51c0-112">The Common Language Specification is defined in Partition I, Clauses 7 through 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span> 

<span data-ttu-id="d51c0-113">Bileşeniniz ortak dil belirtimi uyuyorsa, CLS uyumlu olması garanti ve CLS destekleyen tüm programlama dilinde yazılmıştır derlemelerde koddan erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-113">If your component conforms to the Common Language Specification, it is guaranteed to be CLS-compliant and can be accessed from code in assemblies written in any programming language that supports the CLS.</span></span> <span data-ttu-id="d51c0-114">Bileşeniniz ortak dil belirtimi derleme zamanında uygulayarak uyup uymadığını belirleyebilirsiniz [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği için kaynak kodu.</span><span class="sxs-lookup"><span data-stu-id="d51c0-114">You can determine whether your component conforms to the Common Language Specification at compile time by applying the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute to your source code.</span></span> <span data-ttu-id="d51c0-115">Daha fazla bilgi için bkz: [CLSCompliantAttribute özniteliği](#the-clscompliantattribute-attribute).</span><span class="sxs-lookup"><span data-stu-id="d51c0-115">For more information, see The [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute).</span></span>

<span data-ttu-id="d51c0-116">Bu makalede:</span><span class="sxs-lookup"><span data-stu-id="d51c0-116">In this article:</span></span>

* [<span data-ttu-id="d51c0-117">CLS uyumluluk kuralları</span><span class="sxs-lookup"><span data-stu-id="d51c0-117">CLS compliance rules</span></span>](#cls-compliance-rules)

    * [<span data-ttu-id="d51c0-118">Türleri ve türü üye imzaları</span><span class="sxs-lookup"><span data-stu-id="d51c0-118">Types and type member signatures</span></span>](#types-and-type-member-signatures)

    * [<span data-ttu-id="d51c0-119">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="d51c0-119">Naming conventions</span></span>](#naming-conventions)
    
    * [<span data-ttu-id="d51c0-120">Tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="d51c0-120">Type conversion</span></span>](#type-conversion)
    
    * [<span data-ttu-id="d51c0-121">Diziler</span><span class="sxs-lookup"><span data-stu-id="d51c0-121">Arrays</span></span>](#arrays)
    
    * [<span data-ttu-id="d51c0-122">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="d51c0-122">Interfaces</span></span>](#interfaces)
    
    * [<span data-ttu-id="d51c0-123">Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d51c0-123">Enumerations</span></span>](#enumerations)
    
    * [<span data-ttu-id="d51c0-124">Genel üyeleri yazın</span><span class="sxs-lookup"><span data-stu-id="d51c0-124">Type members in general</span></span>](#type-members-in-general)
    
    * [<span data-ttu-id="d51c0-125">Üye erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="d51c0-125">Member accessibility</span></span>](#member-accessibility)
    
    * [<span data-ttu-id="d51c0-126">Genel türler ve üyeleri</span><span class="sxs-lookup"><span data-stu-id="d51c0-126">Generic types and members</span></span>](#generic-types-and-members)
    
    * [<span data-ttu-id="d51c0-127">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="d51c0-127">Constructors</span></span>](#constructors)
    
    * [<span data-ttu-id="d51c0-128">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-128">Properties</span></span>](#properties)
    
    * [<span data-ttu-id="d51c0-129">Olaylar</span><span class="sxs-lookup"><span data-stu-id="d51c0-129">Events</span></span>](#events)
    
    * [<span data-ttu-id="d51c0-130">Overloads</span><span class="sxs-lookup"><span data-stu-id="d51c0-130">Overloads</span></span>](#overloads)
    
    * [<span data-ttu-id="d51c0-131">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="d51c0-131">Exceptions</span></span>](#exceptions)
    
    * [<span data-ttu-id="d51c0-132">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-132">Attributes</span></span>](#attributes)
    
* [<span data-ttu-id="d51c0-133">CLSCompliantAttribute özniteliği</span><span class="sxs-lookup"><span data-stu-id="d51c0-133">CLSCompliantAttribute attribute</span></span>](#the-clscompliantattribute-attribute)

* [<span data-ttu-id="d51c0-134">Diller arası birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="d51c0-134">Cross-Language Interoperability</span></span>](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a><span data-ttu-id="d51c0-135">CLS uyumluluk kuralları</span><span class="sxs-lookup"><span data-stu-id="d51c0-135">CLS compliance rules</span></span>

<span data-ttu-id="d51c0-136">Bu bölümde, CLS uyumlu bir bileşen oluşturmak için kurallar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-136">This section discusses the rules for creating a CLS-compliant component.</span></span> <span data-ttu-id="d51c0-137">Bölüm ı yan tümcesi 11 / kuralları tam bir listesi için bkz [ECMA-335 standart: ortak dil altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="d51c0-137">For a complete list of rules, see Partition I, Clause 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>

> [!NOTE]
> <span data-ttu-id="d51c0-138">Çerçeveler (dil derleyici oluşturmak için kullandığınız geliştiriciler tüketicilere CLS uyumlu bir bileşen program aracılığıyla erişme (geliştiriciler) uygularken ortak dil belirtimi CLS uyumluluğu için her bir kural açıklanır. CLS-compliant kitaplıklar) ve Extender'larının (dil derleyici veya CLS uyumlu bileşenleri oluşturan bir kod ayrıştırıcı gibi bir araç oluşturan geliştiriciler).</span><span class="sxs-lookup"><span data-stu-id="d51c0-138">The Common Language Specification discusses each rule for CLS compliance as it applies to consumers (developers who are programmatically accessing a component that is CLS-compliant), frameworks (developers who are using a language compiler to create CLS-compliant libraries), and extenders (developers who are creating a tool such as a language compiler or a code parser that creates CLS-compliant components).</span></span> <span data-ttu-id="d51c0-139">Çerçeveler için uygularken bu makalede kurallarında odaklanır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-139">This article focuses on the rules as they apply to frameworks.</span></span> <span data-ttu-id="d51c0-140">Ancak, bazı Extender'larının için geçerli olan kurallar da kullanılarak oluşturulan derlemeleri uygulayabilir Not [Reflection.Emit](xref:System.Reflection.Emit).</span><span class="sxs-lookup"><span data-stu-id="d51c0-140">Note, though, that some of the rules that apply to extenders may also apply to assemblies that are created using [Reflection.Emit](xref:System.Reflection.Emit).</span></span> 

<span data-ttu-id="d51c0-141">Dilden bağımsızdır bir bileşen tasarlamak için yalnızca, bileşenin ortak arabirim CLS uyumluluğu için kurallar uygulama gerekir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-141">To design a component that is language independent, you only need to apply the rules for CLS compliance to your component's public interface.</span></span> <span data-ttu-id="d51c0-142">Özel uygulamanızı belirtimine uygun olarak yok.</span><span class="sxs-lookup"><span data-stu-id="d51c0-142">Your private implementation does not have to conform to the specification.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="d51c0-143">CLS uyumluluğu için kurallar, yalnızca kendi özel uygulama için bir bileşenin ortak arabirimi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-143">The rules for CLS compliance apply only to a component's public interface, not to its private implementation.</span></span> 

<span data-ttu-id="d51c0-144">Örneğin, tamsayılar dışında imzasız [bayt](xref:System.Byte) CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-144">For example, unsigned integers other than [Byte](xref:System.Byte) are not CLS-compliant.</span></span> <span data-ttu-id="d51c0-145">Çünkü `Person` sınıfı aşağıdaki örnekte sunar bir `Age` türündeki özelliği [UInt16](xref:System.UInt16), aşağıdaki kod derleyici uyarısı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d51c0-145">Because the `Person` class in the following example exposes an `Age` property of type [UInt16](xref:System.UInt16), the following code displays a compiler warning.</span></span>

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

<span data-ttu-id="d51c0-146">CLS uyumlu kişi sınıfı türünü değiştirerek yapabilirsiniz `Age` özelliğinden `UInt16` için [Int16](xref:System.Int16), CLS uyumlu, 16 bit işaretli tamsayıyı olduğu.</span><span class="sxs-lookup"><span data-stu-id="d51c0-146">You can make the Person class CLS-compliant by changing the type of `Age` property from `UInt16` to [Int16](xref:System.Int16), which is a CLS-compliant, 16-bit signed integer.</span></span> <span data-ttu-id="d51c0-147">Özel türünü değiştirmek zorunda değilsiniz `personAge` alan.</span><span class="sxs-lookup"><span data-stu-id="d51c0-147">You do not have to change the type of the private `personAge` field.</span></span> 

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

<span data-ttu-id="d51c0-148">Kitaplığın ortak arabirimi aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="d51c0-148">A library's public interface consists of the following:</span></span>

* <span data-ttu-id="d51c0-149">Ortak sınıfları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d51c0-149">Definitions of public classes.</span></span>

* <span data-ttu-id="d51c0-150">Ortak sınıflar ortak üyeleri ve türetilen sınıflar (diğer bir deyişle, korumalı üyeleri) erişilebilir üyelerinin tanımları tanımları.</span><span class="sxs-lookup"><span data-stu-id="d51c0-150">Definitions of the public members of public classes, and definitions of members accessible to derived classes (that is, protected members).</span></span> 

* <span data-ttu-id="d51c0-151">Parametreler ve genel yöntemlerin ortak sınıflar, parametreler ve dönüş türleri ve yöntemleri türetilmiş sınıflara erişilebilir dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="d51c0-151">Parameters and return types of public methods of public classes, and parameters and return types of methods accessible to derived classes.</span></span> 

<span data-ttu-id="d51c0-152">CLS uyumluluğu için kuralları aşağıdaki tabloda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-152">The rules for CLS compliance are listed in the following table.</span></span> <span data-ttu-id="d51c0-153">Kurallar metin alanından verbatim alınır [ECMA-335 standart: ortak dil altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm), telif hakkı 2012 Ecma uluslararası tarafından olduğu.</span><span class="sxs-lookup"><span data-stu-id="d51c0-153">The text of the rules is taken verbatim from the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), which is Copyright 2012 by Ecma International.</span></span> <span data-ttu-id="d51c0-154">Aşağıdaki bölümlerde bu kuralları hakkında daha ayrıntılı bilgi bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="d51c0-154">More detailed information about these rules is found in the following sections.</span></span> 

<span data-ttu-id="d51c0-155">Kategori</span><span class="sxs-lookup"><span data-stu-id="d51c0-155">Category</span></span> | <span data-ttu-id="d51c0-156">Bkz. </span><span class="sxs-lookup"><span data-stu-id="d51c0-156">See</span></span> | <span data-ttu-id="d51c0-157">Kural</span><span class="sxs-lookup"><span data-stu-id="d51c0-157">Rule</span></span> | <span data-ttu-id="d51c0-158">Kural numarası</span><span class="sxs-lookup"><span data-stu-id="d51c0-158">Rule Number</span></span>
-------- | --- | ---- | -----------
<span data-ttu-id="d51c0-159">Erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="d51c0-159">Accessibility</span></span> | [<span data-ttu-id="d51c0-160">Üye erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="d51c0-160">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="d51c0-161">Erişilebilirlik değil değiştirilmesi geçersiz kılma ne zaman bir yöntemini geçersiz kılma farklı bir derlemeden erişilebilirliği devralınan dışında yöntemleri, devralınan zaman `family-or-assembly`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-161">Accessibility shall not be changed when overriding inherited methods, except when overriding a method inherited from a different assembly with accessibility `family-or-assembly`.</span></span> <span data-ttu-id="d51c0-162">Bu durumda, geçersiz kılma erişilebilirlik sahip `family`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-162">In this case, the override shall have accessibility `family`.</span></span> | <span data-ttu-id="d51c0-163">10</span><span class="sxs-lookup"><span data-stu-id="d51c0-163">10</span></span>
<span data-ttu-id="d51c0-164">Erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="d51c0-164">Accessibility</span></span> | [<span data-ttu-id="d51c0-165">Üye erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="d51c0-165">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="d51c0-166">Üye görünür ve erişilebilir olduğunda imza türlerinde herhangi bir üyenin görünür ve erişilebilir olacaktır, görünürlük ve erişilebilirlik türleri ve üyeleri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-166">The visibility and accessibility of types and members shall be such that types in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="d51c0-167">Örneğin, kendi derlemenin dışından görülebilir genel bir yöntem türü yalnızca derlemede görünür olan bir bağımsız değişken sahip.</span><span class="sxs-lookup"><span data-stu-id="d51c0-167">For example, a public method that is visible outside its assembly shall not have an argument whose type is visible only within the assembly.</span></span> <span data-ttu-id="d51c0-168">Üye görünür ve erişilebilir olduğunda görünürlük ve herhangi bir üyenin imzada kullanılan bir oluşturulmuş genel tür oluşturma türlerinin erişilebilirlik görünür ve erişilebilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-168">The visibility and accessibility of types composing an instantiated generic type used in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="d51c0-169">Örneğin, bir oluşturulmuş genel tür imzada mevcut kendi derlemenin dışından görünür bir üyenin türü yalnızca derlemede görünür olan genel bir bağımsız değişken sahip.</span><span class="sxs-lookup"><span data-stu-id="d51c0-169">For example, an instantiated generic type present in the signature of a member that is visible outside its assembly shall not have a generic argument whose type is visible only within the assembly.</span></span> | <span data-ttu-id="d51c0-170">12</span><span class="sxs-lookup"><span data-stu-id="d51c0-170">12</span></span>
<span data-ttu-id="d51c0-171">Diziler</span><span class="sxs-lookup"><span data-stu-id="d51c0-171">Arrays</span></span> | [<span data-ttu-id="d51c0-172">Diziler</span><span class="sxs-lookup"><span data-stu-id="d51c0-172">Arrays</span></span>](#arrays) | <span data-ttu-id="d51c0-173">Diziler CLS uyumlu bir türü olan öğeleri sahip ve tüm boyutlar dizinin alt sınırlarını sıfır sahip.</span><span class="sxs-lookup"><span data-stu-id="d51c0-173">Arrays shall have elements with a CLS-compliant type, and all dimensions of the array shall have lower bounds of zero.</span></span> <span data-ttu-id="d51c0-174">Yalnızca bir dizi ve dizi öğesi türü bir öğedir olgu aşırı arasında ayrım yapmak için gerekli.</span><span class="sxs-lookup"><span data-stu-id="d51c0-174">Only the fact that an item is an array and the element type of the array shall be required to distinguish between overloads.</span></span> <span data-ttu-id="d51c0-175">Ne zaman aşırı yüklemesi iki dayalı olan veya daha fazla dizi öğesi türleri türleri adlı.</span><span class="sxs-lookup"><span data-stu-id="d51c0-175">When overloading is based on two or more array types the element types shall be named types.</span></span> | <span data-ttu-id="d51c0-176">16</span><span class="sxs-lookup"><span data-stu-id="d51c0-176">16</span></span>
<span data-ttu-id="d51c0-177">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-177">Attributes</span></span> | [<span data-ttu-id="d51c0-178">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-178">Attributes</span></span>](#attributes) | <span data-ttu-id="d51c0-179">Öznitelik türü olacaktır [System.Attribute'un](xref:System.Attribute), veya ondan devralan bir tür.</span><span class="sxs-lookup"><span data-stu-id="d51c0-179">Attributes shall be of type [System.Attribute](xref:System.Attribute), or a type inheriting from it.</span></span> | <span data-ttu-id="d51c0-180">41</span><span class="sxs-lookup"><span data-stu-id="d51c0-180">41</span></span>
<span data-ttu-id="d51c0-181">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-181">Attributes</span></span> | [<span data-ttu-id="d51c0-182">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-182">Attributes</span></span>](#attributes) | <span data-ttu-id="d51c0-183">CLS yalnızca bir alt kümesini özel özniteliklerin Kodlamalar izin verir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-183">The CLS only allows a subset of the encodings of custom attributes.</span></span> <span data-ttu-id="d51c0-184">(Bölüm IV bakın) bu Kodlamalar görünür yalnızca türleri şunlardır: [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [ System.Single](xref:System.Single), [System.Double](xref:System.Double), ve herhangi bir numaralandırma türü CLS uyumlu bir temel tamsayı türünde dayanır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-184">The only types that shall appear in these encodings are (see Partition IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), and any enumeration type based on a CLS-compliant base integer type.</span></span> | <span data-ttu-id="d51c0-185">34</span><span class="sxs-lookup"><span data-stu-id="d51c0-185">34</span></span>
<span data-ttu-id="d51c0-186">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-186">Attributes</span></span> | [<span data-ttu-id="d51c0-187">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-187">Attributes</span></span>](#attributes) | <span data-ttu-id="d51c0-188">CLS herkese görünür gerekli değiştiricileri izin verme (`modreq`, Bölüm II bakın), isteğe bağlı değiştiricileri izin vermez ancak (`modopt`, Bölüm II bakın) anlamadığı.</span><span class="sxs-lookup"><span data-stu-id="d51c0-188">The CLS does not allow publicly visible required modifiers (`modreq`, see Partition II), but does allow optional modifiers (`modopt`, see Partition II) it does not understand.</span></span> | <span data-ttu-id="d51c0-189">35</span><span class="sxs-lookup"><span data-stu-id="d51c0-189">35</span></span>
<span data-ttu-id="d51c0-190">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="d51c0-190">Constructors</span></span> | [<span data-ttu-id="d51c0-191">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="d51c0-191">Constructors</span></span>](#constructors) | <span data-ttu-id="d51c0-192">Devralınan örnek veriler için herhangi bir erişim oluşmadan önce bir nesne oluşturucusu bazı örnek oluşturucusu olduğu temel sınıfın çağrısı.</span><span class="sxs-lookup"><span data-stu-id="d51c0-192">An object constructor shall call some instance constructor of its base class before any access occurs to inherited instance data.</span></span> <span data-ttu-id="d51c0-193">(Bu oluşturucular olmak zorunda değildir değer türleri için geçerli değildir.)</span><span class="sxs-lookup"><span data-stu-id="d51c0-193">(This does not apply to value types, which need not have constructors.)</span></span>  | <span data-ttu-id="d51c0-194">21</span><span class="sxs-lookup"><span data-stu-id="d51c0-194">21</span></span>
<span data-ttu-id="d51c0-195">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="d51c0-195">Constructors</span></span> | [<span data-ttu-id="d51c0-196">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="d51c0-196">Constructors</span></span>](#constructors) | <span data-ttu-id="d51c0-197">Bir nesne Oluşturucusu dışındaki bir nesnenin oluşturmanın bir parçası çağrılması değil ve bir nesne iki kez başlatılmamış.</span><span class="sxs-lookup"><span data-stu-id="d51c0-197">An object constructor shall not be called except as part of the creation of an object, and an object shall not be initialized twice.</span></span> | <span data-ttu-id="d51c0-198">22</span><span class="sxs-lookup"><span data-stu-id="d51c0-198">22</span></span>
<span data-ttu-id="d51c0-199">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="d51c0-199">Enumerations</span></span> | [<span data-ttu-id="d51c0-200">Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d51c0-200">Enumerations</span></span>](#enumerations) | <span data-ttu-id="d51c0-201">Enum temel türü bir yerleşik CLS tamsayı türü olacaktır, alanın adını "value__" olacaktır ve bu alan işaretli `RTSpecialName`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-201">The underlying type of an enum shall be a built-in CLS integer type, the name of the field shall be "value__", and that field shall be marked `RTSpecialName`.</span></span> |  <span data-ttu-id="d51c0-202">7</span><span class="sxs-lookup"><span data-stu-id="d51c0-202">7</span></span>
<span data-ttu-id="d51c0-203">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="d51c0-203">Enumerations</span></span> | [<span data-ttu-id="d51c0-204">Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d51c0-204">Enumerations</span></span>](#enumerations) | <span data-ttu-id="d51c0-205">Varlığı veya yokluğuna göre tarafından gösterilen Numaralandırmaların iki farklı tür vardır [System.FlagsAttribute](xref:System.FlagsAttribute) (bkz. Bölüm IV kitaplık) özel bir öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d51c0-205">There are two distinct kinds of enums, indicated by the presence or absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) (see Partition IV Library) custom attribute.</span></span> <span data-ttu-id="d51c0-206">Bir adlandırılmış tamsayı değerlerini temsil eder; diğer temsil adsız bir değer üretmek için birleştirilmiş bir bit bayrakları adlı.</span><span class="sxs-lookup"><span data-stu-id="d51c0-206">One represents named integer values; the other represents named bit flags that can be combined to generate an unnamed value.</span></span> <span data-ttu-id="d51c0-207">Değeri bir `enum` belirtilen değerlere sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-207">The value of an `enum` is not limited to the specified values.</span></span> |  <span data-ttu-id="d51c0-208">8</span><span class="sxs-lookup"><span data-stu-id="d51c0-208">8</span></span>
<span data-ttu-id="d51c0-209">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="d51c0-209">Enumerations</span></span> | [<span data-ttu-id="d51c0-210">Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d51c0-210">Enumerations</span></span>](#enumerations) | <span data-ttu-id="d51c0-211">Bir numaralandırma sabit değeri statik alanları ve enum türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="d51c0-211">Literal static fields of an enum shall have the type of the enum itself.</span></span> |  <span data-ttu-id="d51c0-212">9</span><span class="sxs-lookup"><span data-stu-id="d51c0-212">9</span></span>
<span data-ttu-id="d51c0-213">Olaylar</span><span class="sxs-lookup"><span data-stu-id="d51c0-213">Events</span></span> | [<span data-ttu-id="d51c0-214">Olaylar</span><span class="sxs-lookup"><span data-stu-id="d51c0-214">Events</span></span>](#events) | <span data-ttu-id="d51c0-215">Bir olay uygulamak yöntemleri olarak işaretlenmiş `SpecialName` meta veriler.</span><span class="sxs-lookup"><span data-stu-id="d51c0-215">The methods that implement an event shall be marked `SpecialName` in the metadata.</span></span> |<span data-ttu-id="d51c0-216">29</span><span class="sxs-lookup"><span data-stu-id="d51c0-216">29</span></span>
<span data-ttu-id="d51c0-217">Olaylar</span><span class="sxs-lookup"><span data-stu-id="d51c0-217">Events</span></span> | [<span data-ttu-id="d51c0-218">Olaylar</span><span class="sxs-lookup"><span data-stu-id="d51c0-218">Events</span></span>](#events) | <span data-ttu-id="d51c0-219">Bir olay ve onun erişimciler erişilebilirlik aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-219">The accessibility of an event and of its accessors shall be identical.</span></span> |<span data-ttu-id="d51c0-220">30</span><span class="sxs-lookup"><span data-stu-id="d51c0-220">30</span></span>
<span data-ttu-id="d51c0-221">Olaylar</span><span class="sxs-lookup"><span data-stu-id="d51c0-221">Events</span></span> | [<span data-ttu-id="d51c0-222">Olaylar</span><span class="sxs-lookup"><span data-stu-id="d51c0-222">Events</span></span>](#events) | <span data-ttu-id="d51c0-223">`add` Ve `remove` yöntemleri bir olay ya da her ikisini de gelecektir için mevcut olmalı veya belirtilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-223">The `add` and `remove` methods for an event shall both either be present or absent.</span></span> |<span data-ttu-id="d51c0-224">31</span><span class="sxs-lookup"><span data-stu-id="d51c0-224">31</span></span>
<span data-ttu-id="d51c0-225">Olaylar</span><span class="sxs-lookup"><span data-stu-id="d51c0-225">Events</span></span> | [<span data-ttu-id="d51c0-226">Olaylar</span><span class="sxs-lookup"><span data-stu-id="d51c0-226">Events</span></span>](#events) | <span data-ttu-id="d51c0-227">`add` Ve `remove` yöntemleri bir olay her bir parametre türü alan için olay türünü tanımlar ve bu türetilen [System.Delegate](xref:System.Delegate).</span><span class="sxs-lookup"><span data-stu-id="d51c0-227">The `add` and `remove` methods for an event shall each take one parameter whose type defines the type of the event and that shall be derived from [System.Delegate](xref:System.Delegate).</span></span> |<span data-ttu-id="d51c0-228">32</span><span class="sxs-lookup"><span data-stu-id="d51c0-228">32</span></span>
<span data-ttu-id="d51c0-229">Olaylar</span><span class="sxs-lookup"><span data-stu-id="d51c0-229">Events</span></span> | [<span data-ttu-id="d51c0-230">Olaylar</span><span class="sxs-lookup"><span data-stu-id="d51c0-230">Events</span></span>](#events) | <span data-ttu-id="d51c0-231">Olaylar, belirli bir adlandırma deseni uyması.</span><span class="sxs-lookup"><span data-stu-id="d51c0-231">Events shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="d51c0-232">CLS kural 29 başvurulan SpecialName özniteliği uygun adı karşılaştırmaları göz ardı ve tanımlayıcı kurallarına.</span><span class="sxs-lookup"><span data-stu-id="d51c0-232">The SpecialName attribute referred to in CLS rule 29 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span>  |<span data-ttu-id="d51c0-233">33</span><span class="sxs-lookup"><span data-stu-id="d51c0-233">33</span></span>
<span data-ttu-id="d51c0-234">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="d51c0-234">Exceptions</span></span> | [<span data-ttu-id="d51c0-235">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="d51c0-235">Exceptions</span></span>](#exceptions) | <span data-ttu-id="d51c0-236">Oluşturulan nesnelerin türü olacaktır [System.Exception](xref:System.Exception) veya ondan devralan bir tür.</span><span class="sxs-lookup"><span data-stu-id="d51c0-236">Objects that are thrown shall be of type [System.Exception](xref:System.Exception) or a type inheriting from it.</span></span> <span data-ttu-id="d51c0-237">Öte yandan, CLS uyumlu yöntemlerini diğer tür özel durumlar yayılmasını engellemek için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-237">Nonetheless, CLS-compliant methods are not required to block the propagation of other types of exceptions.</span></span> | <span data-ttu-id="d51c0-238">40</span><span class="sxs-lookup"><span data-stu-id="d51c0-238">40</span></span>
<span data-ttu-id="d51c0-239">Genel</span><span class="sxs-lookup"><span data-stu-id="d51c0-239">General</span></span> | [<span data-ttu-id="d51c0-240">CLS uyumluluk kuralları</span><span class="sxs-lookup"><span data-stu-id="d51c0-240">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="d51c0-241">CLS kuralları erişilebilir veya görünür outsideof tanımlama derleme olan yalnızca parçaları türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-241">CLS rules apply only to those parts of a type that are accessible or visible outsideof the defining assembly.</span></span> | <span data-ttu-id="d51c0-242">1.</span><span class="sxs-lookup"><span data-stu-id="d51c0-242">1</span></span>
<span data-ttu-id="d51c0-243">Genel</span><span class="sxs-lookup"><span data-stu-id="d51c0-243">General</span></span> | [<span data-ttu-id="d51c0-244">CLS uyumluluk kuralları</span><span class="sxs-lookup"><span data-stu-id="d51c0-244">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="d51c0-245">CLS dışı uyumlu türleri üyeleri CLS uyumlu olarak işaretlenmemiş.</span><span class="sxs-lookup"><span data-stu-id="d51c0-245">Members of non-CLS compliant types shall not be marked CLS-compliant.</span></span> | <span data-ttu-id="d51c0-246">2</span><span class="sxs-lookup"><span data-stu-id="d51c0-246">2</span></span>
<span data-ttu-id="d51c0-247">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="d51c0-247">Generics</span></span> | [<span data-ttu-id="d51c0-248">Genel türler ve üyeleri</span><span class="sxs-lookup"><span data-stu-id="d51c0-248">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="d51c0-249">İç içe geçmiş türler en az sayıda genel parametreler kendilerini kapsayan türle sahip.</span><span class="sxs-lookup"><span data-stu-id="d51c0-249">Nested types shall have at least as many generic parameters as the enclosing type.</span></span> <span data-ttu-id="d51c0-250">Genel bir iç içe geçmiş tür parametrelerinde kapsayan türü genel parametreler konuma göre karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-250">Generic parameters in a nested type correspond by position to the generic parameters in its enclosing type.</span></span>  | <span data-ttu-id="d51c0-251">42</span><span class="sxs-lookup"><span data-stu-id="d51c0-251">42</span></span>
<span data-ttu-id="d51c0-252">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="d51c0-252">Generics</span></span> | [<span data-ttu-id="d51c0-253">Genel türler ve üyeleri</span><span class="sxs-lookup"><span data-stu-id="d51c0-253">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="d51c0-254">Genel bir tür adı olmayan iç içe geçmiş türünde bildirilen ya da yeni yukarıda tanımlanan kurallarına göre iç içe yoksa türe giriş türü parametre sayısı kodlayın.</span><span class="sxs-lookup"><span data-stu-id="d51c0-254">The name of a generic type shall encode the number of type parameters declared on the non-nested type, or newly introduced to the type if nested, according to the rules defined above.</span></span> | <span data-ttu-id="d51c0-255">43</span><span class="sxs-lookup"><span data-stu-id="d51c0-255">43</span></span>
<span data-ttu-id="d51c0-256">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="d51c0-256">Generics</span></span> | [<span data-ttu-id="d51c0-257">Genel türler ve üyeleri</span><span class="sxs-lookup"><span data-stu-id="d51c0-257">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="d51c0-258">Genel bir tür kısıtlamalar temel türü veya arabirimleri tarafından genel tür kısıtlamaları getirilmez güvence altına almak için yeterli kısıtlamaları redeclare.</span><span class="sxs-lookup"><span data-stu-id="d51c0-258">A generic type shall redeclare sufficient constraints to guarantee that any constraints on the base type, or interfaces would be satisfied by the generic type constraints.</span></span> | <span data-ttu-id="d51c0-259">44</span><span class="sxs-lookup"><span data-stu-id="d51c0-259">44</span></span>
<span data-ttu-id="d51c0-260">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="d51c0-260">Generics</span></span> | [<span data-ttu-id="d51c0-261">Genel türler ve üyeleri</span><span class="sxs-lookup"><span data-stu-id="d51c0-261">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="d51c0-262">Genel parametreler üzerinde kısıtlamalar olarak kullanılan türleri kendilerini CLS uyumlu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-262">Types used as constraints on generic parameters shall themselves be CLS-compliant.</span></span> | <span data-ttu-id="d51c0-263">45</span><span class="sxs-lookup"><span data-stu-id="d51c0-263">45</span></span>
<span data-ttu-id="d51c0-264">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="d51c0-264">Generics</span></span> | [<span data-ttu-id="d51c0-265">Genel türler ve üyeleri</span><span class="sxs-lookup"><span data-stu-id="d51c0-265">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="d51c0-266">Görünürlük ve bir oluşturulmuş genel tür üyeleri (iç içe geçmiş türler dahil) erişilebilirliğini bir bütün olarak genel tür bildirimi yerine belirli örneklemesi Kapsamınızın dikkate.</span><span class="sxs-lookup"><span data-stu-id="d51c0-266">The visibility and accessibility of members (including nested types) in an instantiated generic type shall be considered to be scoped to the specific instantiation rather than the generic type declaration as a whole.</span></span> <span data-ttu-id="d51c0-267">Bu varsayıldığında, CLS kuralının 12 görünürlük ve erişilebilirlik kuralları hala geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-267">Assuming this, the visibility and accessibility rules of CLS rule 12 still apply.</span></span> | <span data-ttu-id="d51c0-268">46</span><span class="sxs-lookup"><span data-stu-id="d51c0-268">46</span></span>
<span data-ttu-id="d51c0-269">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="d51c0-269">Generics</span></span> | [<span data-ttu-id="d51c0-270">Genel türler ve üyeleri</span><span class="sxs-lookup"><span data-stu-id="d51c0-270">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="d51c0-271">Her soyut veya sanal genel yönteminde var olacaktır varsayılan somut (soyut) uygulama</span><span class="sxs-lookup"><span data-stu-id="d51c0-271">For each abstract or virtual generic method, there shall be a default concrete (nonabstract) implementation</span></span> | <span data-ttu-id="d51c0-272">47</span><span class="sxs-lookup"><span data-stu-id="d51c0-272">47</span></span>
<span data-ttu-id="d51c0-273">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="d51c0-273">Interfaces</span></span> | [<span data-ttu-id="d51c0-274">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="d51c0-274">Interfaces</span></span>](#interfaces) | <span data-ttu-id="d51c0-275">Bunları uygulamak için CLS uyumlu arabirimleri CLS olmayan compliantmethods tanımını gerektirmeyecek.</span><span class="sxs-lookup"><span data-stu-id="d51c0-275">CLS-compliant interfaces shall not require the definition of non-CLS compliantmethods in order to implement them.</span></span> | <span data-ttu-id="d51c0-276">18</span><span class="sxs-lookup"><span data-stu-id="d51c0-276">18</span></span>
<span data-ttu-id="d51c0-277">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="d51c0-277">Interfaces</span></span> | [<span data-ttu-id="d51c0-278">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="d51c0-278">Interfaces</span></span>](#interfaces) | <span data-ttu-id="d51c0-279">CLS uyumlu arabirimlerde statik yöntemler tanımlamak değil ya da alanları tanımla.</span><span class="sxs-lookup"><span data-stu-id="d51c0-279">CLS-compliant interfaces shall not define static methods, nor shall they define fields.</span></span> | <span data-ttu-id="d51c0-280">19</span><span class="sxs-lookup"><span data-stu-id="d51c0-280">19</span></span>
<span data-ttu-id="d51c0-281">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d51c0-281">Members</span></span> | [<span data-ttu-id="d51c0-282">Genel üyeleri yazın</span><span class="sxs-lookup"><span data-stu-id="d51c0-282">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="d51c0-283">Genel statik alanları ve yöntemleri CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-283">Global static fields and methods are not CLS-compliant.</span></span> | <span data-ttu-id="d51c0-284">36</span><span class="sxs-lookup"><span data-stu-id="d51c0-284">36</span></span>
<span data-ttu-id="d51c0-285">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d51c0-285">Members</span></span> | -- | <span data-ttu-id="d51c0-286">Değişmez değer statik değerini alan başlatma meta veri kullanımı ile belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-286">The value of a literal static is specified through the use of field initialization metadata.</span></span> <span data-ttu-id="d51c0-287">CLS uyumlu bir sabit değişmez değeri olarak tam olarak aynı türde alan başlatma meta verilerinde belirtilmiş bir değere sahip olmalıdır (veya bu değişmez değeri ise, temel türde bir `enum`).</span><span class="sxs-lookup"><span data-stu-id="d51c0-287">A CLS-compliant literal must have a value specified in field initialization metadata that is of exactly the same type as the literal (or of the underlying type, if that literal is an `enum`).</span></span> | <span data-ttu-id="d51c0-288">13</span><span class="sxs-lookup"><span data-stu-id="d51c0-288">13</span></span>
<span data-ttu-id="d51c0-289">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d51c0-289">Members</span></span> | [<span data-ttu-id="d51c0-290">Genel üyeleri yazın</span><span class="sxs-lookup"><span data-stu-id="d51c0-290">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="d51c0-291">Vararg kısıtlaması CLS parçası değildir ve yalnızca çağırma kuralı CLS tarafından desteklenen standart çağırma yönetiliyor.</span><span class="sxs-lookup"><span data-stu-id="d51c0-291">The vararg constraint is not part of the CLS, and the only calling convention supported by the CLS is the standard managed calling convention.</span></span> | <span data-ttu-id="d51c0-292">15</span><span class="sxs-lookup"><span data-stu-id="d51c0-292">15</span></span>
<span data-ttu-id="d51c0-293">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="d51c0-293">Naming conventions</span></span> | [<span data-ttu-id="d51c0-294">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="d51c0-294">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="d51c0-295">Derlemeleri eki 7, teknik rapor 15 başlatmak ve tanımlayıcılarının, kullanılabilir adresindeki çevrimiçi dahil edilmesi için izin verilen karakter kümesini yöneten Unicode Standard3.0 izleyin [Unicode normalleştirme formları](http://www.unicode.org/unicode/reports/tr15/tr15-18.html).</span><span class="sxs-lookup"><span data-stu-id="d51c0-295">Assemblies shall follow Annex 7 of Technical Report 15 of the Unicode Standard3.0 governing the set of characters permitted to start and be included in identifiers, available online at [Unicode Normalization Forms](http://www.unicode.org/unicode/reports/tr15/tr15-18.html).</span></span> <span data-ttu-id="d51c0-296">Tanımlayıcıları Unicode normalleştirme Form c tarafından tanımlanan kurallı biçimde olacaktır CLS amacıyla iki tanımlayıcılara aynı küçük eşlemelerini (Unicode yerel duyarsız, bire bir küçük harf eşlemeleri tarafından belirtildiği şekilde) aynı olması durumunda.</span><span class="sxs-lookup"><span data-stu-id="d51c0-296">Identifiers shall be in the canonical format defined by Unicode Normalization Form C. For CLS purposes, two identifiersare the same if their lowercase mappings (as specified by the Unicode locale-insensitive, one-to-one lowercase mappings) are the same.</span></span> <span data-ttu-id="d51c0-297">Diğer bir deyişle, CLS altında farklı olarak kabul edilmesi iki tanımlayıcıları için bunların birden fazla yalnızca kendi durumda farklı.</span><span class="sxs-lookup"><span data-stu-id="d51c0-297">That is, for two identifiers to be considered different under the CLS they shall differ in more than simply their case.</span></span> <span data-ttu-id="d51c0-298">Ancak, devralınan bir tanımı geçersiz kılmak için CLI özgün bildirimi kesin kodlama kullanılabilir gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-298">However, in order to override an inherited definition the CLI requires the precise encoding of the original declaration be used.</span></span> | <span data-ttu-id="d51c0-299">4</span><span class="sxs-lookup"><span data-stu-id="d51c0-299">4</span></span>
<span data-ttu-id="d51c0-300">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="d51c0-300">Overloading</span></span> | [<span data-ttu-id="d51c0-301">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="d51c0-301">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="d51c0-302">Tüm adları CLS uyumlu bir kapsamda sunulan ayrı bağımsız tür adları aynı ve aşırı yükleme aracılığıyla çözümlenmiş nerede dışında tutulamaz.</span><span class="sxs-lookup"><span data-stu-id="d51c0-302">All names introduced in a CLS-compliant scope shall be distinct independent of kind, except where the names are identical and resolved via overloading.</span></span> <span data-ttu-id="d51c0-303">CTS sağlar, ancak bir yöntem ve bir alan için aynı adı kullanmak tek bir türü diğer bir deyişle, CLS desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d51c0-303">That is, while the CTS allows a single type to use the same name for a method and a field, the CLS does not.</span></span> | <span data-ttu-id="d51c0-304">5</span><span class="sxs-lookup"><span data-stu-id="d51c0-304">5</span></span>
<span data-ttu-id="d51c0-305">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="d51c0-305">Overloading</span></span> | [<span data-ttu-id="d51c0-306">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="d51c0-306">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="d51c0-307">Alanlar ve iç içe geçmiş türler tarafından tanımlayıcı karşılaştırma tek başına farklı olacaktır, ayırt edici olarak ayrı imzaları eventhough CTS sağlar.</span><span class="sxs-lookup"><span data-stu-id="d51c0-307">Fields and nested types shall be distinct by identifier comparison alone, eventhough the CTS allows distinct signatures to be distinguished.</span></span> <span data-ttu-id="d51c0-308">Yöntemler, özellikler ve (tanımlayıcı karşılaştırma tarafından) aynı ada sahip olayları dönüş türüne göre çok daha fazlası farklı dışındaki CLS kural 39 belirtildiği gibi</span><span class="sxs-lookup"><span data-stu-id="d51c0-308">Methods, properties, and events that have the same name (by identifier comparison) shall differ by more than just the return type,except as specified in CLS Rule 39</span></span> | <span data-ttu-id="d51c0-309">6</span><span class="sxs-lookup"><span data-stu-id="d51c0-309">6</span></span>
<span data-ttu-id="d51c0-310">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="d51c0-310">Overloading</span></span> | [<span data-ttu-id="d51c0-311">Overloads</span><span class="sxs-lookup"><span data-stu-id="d51c0-311">Overloads</span></span>](#overloads) | <span data-ttu-id="d51c0-312">Yalnızca özelliklerini ve yöntemlerini aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="d51c0-312">Only properties and methods can be overloaded.</span></span> | <span data-ttu-id="d51c0-313">37</span><span class="sxs-lookup"><span data-stu-id="d51c0-313">37</span></span>
<span data-ttu-id="d51c0-314">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="d51c0-314">Overloading</span></span> | [<span data-ttu-id="d51c0-315">Overloads</span><span class="sxs-lookup"><span data-stu-id="d51c0-315">Overloads</span></span>](#overloads) |<span data-ttu-id="d51c0-316">Özellikleri ve yöntemleri aşırı yüklenebilir yalnızca sayısı ve türleri adlı dönüşüm işleçleri dışında kendi parametreleri temel `op_Implicit` ve `op_Explicit`, kendi dönüş türüne bağlı olarak, aynı zamanda aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-316">Properties and methods can be overloaded based only on the number and types of their parameters, except the conversion operators named `op_Implicit` and `op_Explicit`, which can also be overloaded based on their return type.</span></span> | <span data-ttu-id="d51c0-317">38</span><span class="sxs-lookup"><span data-stu-id="d51c0-317">38</span></span>
<span data-ttu-id="d51c0-318">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="d51c0-318">Overloading</span></span> | -- | <span data-ttu-id="d51c0-319">İki veya daha fazla CLS uyumlu yöntemler tür tarafından bildirilen aynı sistemine sahip, türü örneklemesi, belirli bir dizi için aynı parametre ve dönüş türleri, sonra bu yöntemler bu tür örneklemesi anlam olarak eşdeğer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-319">If two or more CLS-compliant methods declared in a type have the same nameand, for a specific set of type instantiations, they have the same parameter and return types, then all these methods shall be semantically equivalent at those type instantiations.</span></span> | <span data-ttu-id="d51c0-320">48</span><span class="sxs-lookup"><span data-stu-id="d51c0-320">48</span></span>
<span data-ttu-id="d51c0-321">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-321">Properties</span></span> | [<span data-ttu-id="d51c0-322">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-322">Properties</span></span>](#properties) | <span data-ttu-id="d51c0-323">Bir özelliğin'Set ' yordamı yöntemleri uygulamak yöntemleri olarak işaretlenmiş `SpecialName` meta veriler.</span><span class="sxs-lookup"><span data-stu-id="d51c0-323">The methods that implement the getter and setter methods of a property shall be marked `SpecialName` in the metadata.</span></span> | <span data-ttu-id="d51c0-324">24</span><span class="sxs-lookup"><span data-stu-id="d51c0-324">24</span></span>
<span data-ttu-id="d51c0-325">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-325">Properties</span></span> | [<span data-ttu-id="d51c0-326">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-326">Properties</span></span>](#properties) | <span data-ttu-id="d51c0-327">Bir özelliğin erişimciler tüm statik olacaktır, tüm sanal veya tüm örneği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-327">A property’s accessors shall all be static, all be virtual, or all be instance.</span></span> | <span data-ttu-id="d51c0-328">26</span><span class="sxs-lookup"><span data-stu-id="d51c0-328">26</span></span>
<span data-ttu-id="d51c0-329">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-329">Properties</span></span> | [<span data-ttu-id="d51c0-330">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-330">Properties</span></span>](#properties) | <span data-ttu-id="d51c0-331">Bir özelliğin türünü alıcı dönüş türü ve kurucu son bağımsız değişkeni tür olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-331">The type of a property shall be the return type of the getter and the type of the last argument of the setter.</span></span> <span data-ttu-id="d51c0-332">Özelliğin parametre türlerini alıcı ve tüm türleri parametreleri ancak kurucu son parametre türleri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-332">The types of the parameters of the property shall be the types of the parameters to the getter and the types of all but the final parameter of the setter.</span></span> <span data-ttu-id="d51c0-333">Tüm bu tür CLS uyumlu olacaktır ve yönetilen işaretçileri tutulamaz (diğer bir deyişle, başvuruya göre geçirilmesi değil).</span><span class="sxs-lookup"><span data-stu-id="d51c0-333">All of these types shall be CLS-compliant, and shall not be managed pointers (that is, shall not be passed by reference).</span></span> | <span data-ttu-id="d51c0-334">27</span><span class="sxs-lookup"><span data-stu-id="d51c0-334">27</span></span>
<span data-ttu-id="d51c0-335">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-335">Properties</span></span> | [<span data-ttu-id="d51c0-336">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-336">Properties</span></span>](#properties) | <span data-ttu-id="d51c0-337">Özellikler, belirli bir adlandırma deseni uyması.</span><span class="sxs-lookup"><span data-stu-id="d51c0-337">Properties shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="d51c0-338">`SpecialName` CLS kural 24 başvuruda bulunulan öznitelik uygun adı karşılaştırmaları göz ardı ve tanımlayıcı kurallarına.</span><span class="sxs-lookup"><span data-stu-id="d51c0-338">The `SpecialName` attribute referred to in CLS rule 24 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span> <span data-ttu-id="d51c0-339">Özellik alıcısı yöntemi, ayarlayıcı yöntemi veya ikisine birden sahip.</span><span class="sxs-lookup"><span data-stu-id="d51c0-339">A property shall have a getter method, a setter method, or both.</span></span> | <span data-ttu-id="d51c0-340">28</span><span class="sxs-lookup"><span data-stu-id="d51c0-340">28</span></span>
<span data-ttu-id="d51c0-341">Tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="d51c0-341">Type conversion</span></span> | [<span data-ttu-id="d51c0-342">Tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="d51c0-342">Type conversion</span></span>](#type-conversion) | <span data-ttu-id="d51c0-343">Op_Implicit veya op_Explicit sağlanırsa, zorlama sağlama alternatif bir yol sağlanan.</span><span class="sxs-lookup"><span data-stu-id="d51c0-343">If either op_Implicit or op_Explicit is provided, an alternate means of providing the coercion shall be provided.</span></span> | <span data-ttu-id="d51c0-344">39</span><span class="sxs-lookup"><span data-stu-id="d51c0-344">39</span></span>
<span data-ttu-id="d51c0-345">Türler</span><span class="sxs-lookup"><span data-stu-id="d51c0-345">Types</span></span> | [<span data-ttu-id="d51c0-346">Türleri ve türü üye imzaları</span><span class="sxs-lookup"><span data-stu-id="d51c0-346">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="d51c0-347">Paketlenmiş değer türleri CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-347">Boxed value types are not CLS-compliant.</span></span> | <span data-ttu-id="d51c0-348">3</span><span class="sxs-lookup"><span data-stu-id="d51c0-348">3</span></span>
<span data-ttu-id="d51c0-349">Türler</span><span class="sxs-lookup"><span data-stu-id="d51c0-349">Types</span></span> | [<span data-ttu-id="d51c0-350">Türleri ve türü üye imzaları</span><span class="sxs-lookup"><span data-stu-id="d51c0-350">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="d51c0-351">İmza görünen tüm türleri CLS uyumlu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-351">All types appearing in a signature shall be CLS-compliant.</span></span> <span data-ttu-id="d51c0-352">Bir oluşturulmuş genel tür oluşturma tüm türleri CLS uyumlu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-352">All types composing an instantiated generic type shall be CLS-compliant.</span></span> | <span data-ttu-id="d51c0-353">11</span><span class="sxs-lookup"><span data-stu-id="d51c0-353">11</span></span>
<span data-ttu-id="d51c0-354">Türler</span><span class="sxs-lookup"><span data-stu-id="d51c0-354">Types</span></span> | [<span data-ttu-id="d51c0-355">Türleri ve türü üye imzaları</span><span class="sxs-lookup"><span data-stu-id="d51c0-355">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="d51c0-356">Belirlenmiş başvurular CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-356">Typed references are not CLS-compliant.</span></span> | <span data-ttu-id="d51c0-357">14</span><span class="sxs-lookup"><span data-stu-id="d51c0-357">14</span></span>
<span data-ttu-id="d51c0-358">Türler</span><span class="sxs-lookup"><span data-stu-id="d51c0-358">Types</span></span> | [<span data-ttu-id="d51c0-359">Türleri ve türü üye imzaları</span><span class="sxs-lookup"><span data-stu-id="d51c0-359">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="d51c0-360">Yönetilmeyen işaretçi türleri CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-360">Unmanaged pointer types are not CLS-compliant.</span></span> | <span data-ttu-id="d51c0-361">17</span><span class="sxs-lookup"><span data-stu-id="d51c0-361">17</span></span>
<span data-ttu-id="d51c0-362">Türler</span><span class="sxs-lookup"><span data-stu-id="d51c0-362">Types</span></span> | [<span data-ttu-id="d51c0-363">Türleri ve türü üye imzaları</span><span class="sxs-lookup"><span data-stu-id="d51c0-363">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="d51c0-364">CLS uyumlu sınıfları, değer türleri ve arabirimleri CLS uyumlu olmayan üyeler uyarlamasını gerektirmeyecek</span><span class="sxs-lookup"><span data-stu-id="d51c0-364">CLS-compliant classes, value types, and interfaces shall not require the implementation of non-CLS-compliant members</span></span> | <span data-ttu-id="d51c0-365">20</span><span class="sxs-lookup"><span data-stu-id="d51c0-365">20</span></span>
<span data-ttu-id="d51c0-366">Türler</span><span class="sxs-lookup"><span data-stu-id="d51c0-366">Types</span></span> | [<span data-ttu-id="d51c0-367">Türleri ve türü üye imzaları</span><span class="sxs-lookup"><span data-stu-id="d51c0-367">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="d51c0-368">[System.Object](xref:System.Object) CLS uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="d51c0-368">[System.Object](xref:System.Object) is CLS-compliant.</span></span> <span data-ttu-id="d51c0-369">CLS uyumlu herhangi bir sınıf CLS uyumlu bir sınıftan devralınan.</span><span class="sxs-lookup"><span data-stu-id="d51c0-369">Any other CLS-compliant class shall inherit from a CLS-compliant class.</span></span> | <span data-ttu-id="d51c0-370">23</span><span class="sxs-lookup"><span data-stu-id="d51c0-370">23</span></span>

### <a name="types-and-type-member-signatures"></a><span data-ttu-id="d51c0-371">Türleri ve türü üye imzaları</span><span class="sxs-lookup"><span data-stu-id="d51c0-371">Types and type member signatures</span></span>

<span data-ttu-id="d51c0-372">[System.Object](xref:System.Object) türü CLS uyumlu olduğundan ve .NET Framework türü sistemindeki tüm nesne türlerini taban türü değil.</span><span class="sxs-lookup"><span data-stu-id="d51c0-372">The [System.Object](xref:System.Object) type is CLS-compliant and is the base type of all object types in the .NET Framework type system.</span></span> <span data-ttu-id="d51c0-373">.NET Framework'teki devralma olduğu ya da örtük (örneğin, [dize](xref:System.String) örtük olarak sınıfının devraldığı `Object` sınıfı) veya açık (örneğin, [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) sınıf açıkça devralır [ArgumentException](xref:System.ArgumentException) açıkça devraldığı sınıfı [özel durum](xref:System.Exception) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d51c0-373">Inheritance in the .NET Framework is either implicit (for example, the [String](xref:System.String) class implicitly inherits from the `Object` class) or explicit (for example, the [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) class explicitly inherits from the [ArgumentException](xref:System.ArgumentException) class, which explicitly inherits from the [Exception](xref:System.Exception) class.</span></span> <span data-ttu-id="d51c0-374">CLS uyumlu olacak şekilde türetilen tür için temel türü de CLS uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-374">For a derived type to be CLS compliant, its base type must also be CLS-compliant.</span></span> 

<span data-ttu-id="d51c0-375">Aşağıdaki örnek, temel türü CLS uyumlu olmayan türetilmiş bir tür gösterir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-375">The following example shows a derived type whose base type is not CLS-compliant.</span></span> <span data-ttu-id="d51c0-376">Bir taban tanımlar `Counter` işaretsiz bir 32 bit tamsayı sayacı olarak kullanan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d51c0-376">It defines a base `Counter` class that uses an unsigned 32-bit integer as a counter.</span></span> <span data-ttu-id="d51c0-377">Sınıfı, bir işaretsiz tamsayı kaydırma tarafından sayaç işlevselliği sağladığından, sınıf-CLS uyumlu olmayan olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-377">Because the class provides counter functionality by wrapping an unsigned integer, the class is marked as non-CLS-compliant.</span></span> <span data-ttu-id="d51c0-378">Sonuç olarak, türetilmiş bir sınıf `NonZeroCounter`, ayrıca CLS uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="d51c0-378">As a result, a derived class, `NonZeroCounter`, is also not CLS-compliant.</span></span> 

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
      return String.Format("{0}). ", ctr);
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
      Return String.Format("{0}). ", ctr)
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

<span data-ttu-id="d51c0-379">Bir yöntemin dönüş türü veya bir özellik türü de dahil olmak üzere üye imzalarında görünür tüm türleri CLS ile uyumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-379">All types that appear in member signatures, including a method's return type or a property type, must be CLS-compliant.</span></span> <span data-ttu-id="d51c0-380">Ayrıca, genel türleri için:</span><span class="sxs-lookup"><span data-stu-id="d51c0-380">In addition, for generic types:</span></span> 

* <span data-ttu-id="d51c0-381">Oluşturulan genel bir tür oluşturan tüm türleri CLS ile uyumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-381">All types that compose an instantiated generic type must be CLS-compliant.</span></span>

* <span data-ttu-id="d51c0-382">Genel parametreler üzerinde kısıtlamalar olarak kullanılan tüm türleri CLS ile uyumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-382">All types used as constraints on generic parameters must be CLS-compliant.</span></span> 

<span data-ttu-id="d51c0-383">.NET [ortak tür sistemi](common-type-system.md) bir derlemenin meta verilerde doğrudan ortak dil çalışma zamanı tarafından desteklenir ve özel olarak kodlanmış yerleşik türler içerir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-383">The .NET [common type system](common-type-system.md) includes a number of built-in types that are supported directly by the common language runtime and are specially encoded in an assembly's metadata.</span></span> <span data-ttu-id="d51c0-384">İç bu tür, aşağıdaki tabloda listelenen CLS uyumlu türleridir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-384">Of these intrinsic types, the types listed in the following table are CLS-compliant.</span></span> 


<span data-ttu-id="d51c0-385">CLS uyumlu türü</span><span class="sxs-lookup"><span data-stu-id="d51c0-385">CLS-compliant type</span></span> | <span data-ttu-id="d51c0-386">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d51c0-386">Description</span></span>
------------------ | -----------
[<span data-ttu-id="d51c0-387">Bayt</span><span class="sxs-lookup"><span data-stu-id="d51c0-387">Byte</span></span>](xref:System.Byte) | <span data-ttu-id="d51c0-388">8 bit işaretsiz tamsayıyı</span><span class="sxs-lookup"><span data-stu-id="d51c0-388">8-bit unsigned integer</span></span> 
[<span data-ttu-id="d51c0-389">Int16</span><span class="sxs-lookup"><span data-stu-id="d51c0-389">Int16</span></span>](xref:System.Int16) | <span data-ttu-id="d51c0-390">16 bit işaretli tamsayıyı</span><span class="sxs-lookup"><span data-stu-id="d51c0-390">16-bit signed integer</span></span> 
[<span data-ttu-id="d51c0-391">Int32</span><span class="sxs-lookup"><span data-stu-id="d51c0-391">Int32</span></span>](xref:System.Int32) | <span data-ttu-id="d51c0-392">32 bit işaretli tamsayıyı</span><span class="sxs-lookup"><span data-stu-id="d51c0-392">32-bit signed integer</span></span> 
[<span data-ttu-id="d51c0-393">Int64</span><span class="sxs-lookup"><span data-stu-id="d51c0-393">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="d51c0-394">64 bit işaretli tamsayıyı</span><span class="sxs-lookup"><span data-stu-id="d51c0-394">64-bit signed integer</span></span>
[<span data-ttu-id="d51c0-395">Tek</span><span class="sxs-lookup"><span data-stu-id="d51c0-395">Single</span></span>](xref:System.Single) | <span data-ttu-id="d51c0-396">Tek duyarlıklı kayan noktalı değeri</span><span class="sxs-lookup"><span data-stu-id="d51c0-396">Single-precision floating-point value</span></span>
[<span data-ttu-id="d51c0-397">Çift</span><span class="sxs-lookup"><span data-stu-id="d51c0-397">Double</span></span>](xref:System.Double) | <span data-ttu-id="d51c0-398">Çift duyarlıklı kayan noktalı değeri</span><span class="sxs-lookup"><span data-stu-id="d51c0-398">Double-precision floating-point value</span></span>
[<span data-ttu-id="d51c0-399">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d51c0-399">Boolean</span></span>](xref:System.Boolean) | <span data-ttu-id="d51c0-400">TRUE veya false değeri türü</span><span class="sxs-lookup"><span data-stu-id="d51c0-400">true or false value type</span></span> 
[<span data-ttu-id="d51c0-401">char</span><span class="sxs-lookup"><span data-stu-id="d51c0-401">Char</span></span>](xref:System.Char) | <span data-ttu-id="d51c0-402">UTF-16 kodlu kod birimi</span><span class="sxs-lookup"><span data-stu-id="d51c0-402">UTF-16 encoded code unit</span></span>
[<span data-ttu-id="d51c0-403">Ondalık</span><span class="sxs-lookup"><span data-stu-id="d51c0-403">Decimal</span></span>](xref:System.Decimal) | <span data-ttu-id="d51c0-404">Olmayan kayan noktalı ondalık sayı</span><span class="sxs-lookup"><span data-stu-id="d51c0-404">Non-floating-point decimal number</span></span>
[<span data-ttu-id="d51c0-405">IntPtr</span><span class="sxs-lookup"><span data-stu-id="d51c0-405">IntPtr</span></span>](xref:System.IntPtr) | <span data-ttu-id="d51c0-406">İşaretçi veya platform tarafından tanımlanan bir boyut tanıtıcısı</span><span class="sxs-lookup"><span data-stu-id="d51c0-406">Pointer or handle of a platform-defined size</span></span>
[<span data-ttu-id="d51c0-407">Dize</span><span class="sxs-lookup"><span data-stu-id="d51c0-407">String</span></span>](xref:System.String) | <span data-ttu-id="d51c0-408">Sıfır, bir veya daha fazla karakter nesneleri koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="d51c0-408">Collection of zero, one, or more Char objects</span></span> 
 
<span data-ttu-id="d51c0-409">Aşağıdaki tabloda listelenen iç türleri CLS uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="d51c0-409">The intrinsic types listed in the following table are not CLS-Compliant.</span></span>


<span data-ttu-id="d51c0-410">Uyumlu türü</span><span class="sxs-lookup"><span data-stu-id="d51c0-410">Non-compliant type</span></span> | <span data-ttu-id="d51c0-411">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d51c0-411">Description</span></span> | <span data-ttu-id="d51c0-412">CLS uyumlu alternatifi</span><span class="sxs-lookup"><span data-stu-id="d51c0-412">CLS-compliant alternative</span></span>
------------------ | ----------- | -------------------------
[<span data-ttu-id="d51c0-413">SByte</span><span class="sxs-lookup"><span data-stu-id="d51c0-413">SByte</span></span>](xref:System.SByte) | <span data-ttu-id="d51c0-414">8 bit işaretli tamsayıyı veri türü</span><span class="sxs-lookup"><span data-stu-id="d51c0-414">8-bit signed integer data type</span></span> | [<span data-ttu-id="d51c0-415">Int16</span><span class="sxs-lookup"><span data-stu-id="d51c0-415">Int16</span></span>](xref:System.Int16)
[<span data-ttu-id="d51c0-416">UInt16</span><span class="sxs-lookup"><span data-stu-id="d51c0-416">UInt16</span></span>](xref:System.UInt16) | <span data-ttu-id="d51c0-417">16 bit işaretsiz tamsayıyı</span><span class="sxs-lookup"><span data-stu-id="d51c0-417">16-bit unsigned integer</span></span> | [<span data-ttu-id="d51c0-418">Int32</span><span class="sxs-lookup"><span data-stu-id="d51c0-418">Int32</span></span>](xref:System.Int32)
[<span data-ttu-id="d51c0-419">UInt32</span><span class="sxs-lookup"><span data-stu-id="d51c0-419">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="d51c0-420">32 bit işaretsiz tamsayıyı</span><span class="sxs-lookup"><span data-stu-id="d51c0-420">32-bit unsigned integer</span></span> | [<span data-ttu-id="d51c0-421">Int64</span><span class="sxs-lookup"><span data-stu-id="d51c0-421">Int64</span></span>](xref:System.Int64)
[<span data-ttu-id="d51c0-422">UInt64</span><span class="sxs-lookup"><span data-stu-id="d51c0-422">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="d51c0-423">64 bit işaretsiz tamsayıyı</span><span class="sxs-lookup"><span data-stu-id="d51c0-423">64-bit unsigned integer</span></span> | <span data-ttu-id="d51c0-424">[Int64](xref:System.Int64) (taşma), [BigInteger](xref:System.Numerics.BigInteger), veya [çift](xref:System.Double)</span><span class="sxs-lookup"><span data-stu-id="d51c0-424">[Int64](xref:System.Int64) (may overflow), [BigInteger](xref:System.Numerics.BigInteger), or [Double](xref:System.Double)</span></span>
[<span data-ttu-id="d51c0-425">UIntPtr</span><span class="sxs-lookup"><span data-stu-id="d51c0-425">UIntPtr</span></span>](xref:System.UIntPtr) | <span data-ttu-id="d51c0-426">İmzasız işaretçi veya tanıtıcısı</span><span class="sxs-lookup"><span data-stu-id="d51c0-426">Unsigned pointer or handle</span></span> | [<span data-ttu-id="d51c0-427">IntPtr</span><span class="sxs-lookup"><span data-stu-id="d51c0-427">IntPtr</span></span>](xref:System.IntPtr)
 
 <span data-ttu-id="d51c0-428">.NET Framework sınıf kitaplığı veya başka bir sınıf kitaplığı CLS ile uyumlu olmayan diğer türleri içerebilir; Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d51c0-428">The .NET Framework Class Library or any other class library may include other types that aren't CLS-compliant; for example:</span></span> 
 
 * <span data-ttu-id="d51c0-429">Paketlenmiş değer türleri.</span><span class="sxs-lookup"><span data-stu-id="d51c0-429">Boxed value types.</span></span> <span data-ttu-id="d51c0-430">Aşağıdaki C# örnek türünde ortak bir özelliği olan bir sınıfı oluşturur `int`\* adlı `Value`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-430">The following C# example creates a class that has a public property of type `int`\* named `Value`.</span></span> <span data-ttu-id="d51c0-431">Çünkü bir `int`\* paketlenmiş değer türü derleyici-CLS uyumlu olmayan olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="d51c0-431">Because an `int`\* is a boxed value type, the compiler flags it as non-CLS-compliant.</span></span>

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

* <span data-ttu-id="d51c0-432">Bir nesneye başvuru ve türüne bir başvuru içeren özel yapılar belirlenmiş başvurular.</span><span class="sxs-lookup"><span data-stu-id="d51c0-432">Typed references, which are special constructs that contain a reference to an object and a reference to a type.</span></span>

<span data-ttu-id="d51c0-433">Bir tür CLS ile uyumlu değilse, uygulamalıdır [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) ile öznitelik bir *isCompliant* parametre değeriyle `false` ona.</span><span class="sxs-lookup"><span data-stu-id="d51c0-433">If a type is not CLS-compliant, you should apply the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute with an *isCompliant* parameter with a value of `false` to it.</span></span> <span data-ttu-id="d51c0-434">Daha fazla bilgi için bkz: [CLSCompliantAttribute özniteliği](#the-clscompliantattribute-attribute) bölümü.</span><span class="sxs-lookup"><span data-stu-id="d51c0-434">For more information, see the [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute) section.</span></span>  

<span data-ttu-id="d51c0-435">Aşağıdaki örnek, CLS uyumluluğu yöntem imzası ve genel tür oluşturmada sorun gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-435">The following example illustrates the problem of CLS compliance in a method signature and in generic type instantiation.</span></span> <span data-ttu-id="d51c0-436">Tanımladığı bir `InvoiceItem` türünde bir özellik sınıfıyla [UInt32](xref:System.UInt32), türünde bir özellik [null atanabilir, (UInt32)](xref:System.Nullable%601)hem de türünde parametrelere sahip bir oluşturucu `UInt32` ve `Nullable(Of UInt32)`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-436">It defines an `InvoiceItem` class with a property of type [UInt32](xref:System.UInt32), a property of type [Nullable(Of UInt32)](xref:System.Nullable%601), and a constructor with parameters of type `UInt32` and `Nullable(Of UInt32)`.</span></span> <span data-ttu-id="d51c0-437">Bu örneği derlemek çalıştığınızda dört derleyici uyarıları alın.</span><span class="sxs-lookup"><span data-stu-id="d51c0-437">You get four compiler warnings when you try to compile this example.</span></span>

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

<span data-ttu-id="d51c0-438">Derleyici uyarılarını kaldırmak için CLS uyumlu olmayan türler yerini `InvoiceItem` uyumlu türleri olan ortak arabirim:</span><span class="sxs-lookup"><span data-stu-id="d51c0-438">To eliminate the compiler warnings, replace the non-CLS-compliant types in the `InvoiceItem` public interface with compliant types:</span></span>

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

<span data-ttu-id="d51c0-439">Listelenen belirli türlerine ek olarak bazı kategorileri türlerinin CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-439">In addition to the specific types listed, some categories of types are not CLS compliant.</span></span> <span data-ttu-id="d51c0-440">Bu, yönetilmeyen işaretçi türleri ve işlev işaretçisi türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-440">These include unmanaged pointer types and function pointer types.</span></span> <span data-ttu-id="d51c0-441">Aşağıdaki örnek, dizisi oluşturmak için bir işaretçi bir tamsayıya kullandığından derleyici uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d51c0-441">The following example generates a compiler warning because it uses a pointer to an integer to create an array of integers.</span></span> 

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

```vb
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

<span data-ttu-id="d51c0-442">CLS uyumlu için soyut sınıflar (diğer bir deyişle, sınıflar olarak işaretlenmiş `abstract` C#), sınıfın tüm üyelerini de CLS ile uyumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-442">For CLS-compliant abstract classes (that is, classes marked as `abstract` in C#), all members of the class must also be CLS-compliant.</span></span> 

### <a name="naming-conventions"></a><span data-ttu-id="d51c0-443">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="d51c0-443">Naming conventions</span></span>

<span data-ttu-id="d51c0-444">Bazı programlama dilleri büyük/küçük harfe duyarsızdır olduğundan (örneğin, ad alanlarını, türleri ve üyeleri adları) tanımlayıcılar örnekten daha fazla farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-444">Because some programming languages are case-insensitive, identifiers (such as the names of namespaces, types, and members) must differ by more than case.</span></span> <span data-ttu-id="d51c0-445">İki tanımlayıcı küçük eşlemelerini aynıysa eşdeğer olarak değerlendiriliyor.</span><span class="sxs-lookup"><span data-stu-id="d51c0-445">Two identifiers are considered equivalent if their lowercase mappings are the same.</span></span> <span data-ttu-id="d51c0-446">Aşağıdaki C# örnek iki ortak sınıf tanımlar `Person` ve `person`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-446">The following C# example defines two public classes, `Person` and `person`.</span></span> <span data-ttu-id="d51c0-447">Yalnızca örneğe göre farklılık gösterdiğinden, C# Derleyici bunları değil CLS uyumlu işaretler.</span><span class="sxs-lookup"><span data-stu-id="d51c0-447">Because they differ only by case, the C# compiler flags them as not CLS-compliant.</span></span> 

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

<span data-ttu-id="d51c0-448">Ad alanlarını, türleri ve üyeleri, adları gibi Dil tanımlayıcıları programlama gerekir uygun [Unicode standart 3.0, teknik rapor 15, eki 7](https://www.unicode.org/reports/tr15/tr15-18.html).</span><span class="sxs-lookup"><span data-stu-id="d51c0-448">Programming language identifiers, such as the names of namespaces, types, and members, must conform to the [Unicode Standard 3.0, Technical Report 15, Annex 7](https://www.unicode.org/reports/tr15/tr15-18.html).</span></span> <span data-ttu-id="d51c0-449">Bunun anlamı:</span><span class="sxs-lookup"><span data-stu-id="d51c0-449">This means that:</span></span>

* <span data-ttu-id="d51c0-450">İlk karakteri bir tanımlayıcı olarak herhangi bir Unicode büyük harf, küçük harf, büyük/küçük harf başlık, değiştiricisi, diğer mektup olması veya numarası harf.</span><span class="sxs-lookup"><span data-stu-id="d51c0-450">The first character of an identifier can be any Unicode uppercase letter, lowercase letter, title case letter, modifier letter, other letter, or letter number.</span></span> <span data-ttu-id="d51c0-451">Unicode karakter kategorileri hakkında daha fazla bilgi için bkz: [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="d51c0-451">For information on Unicode character categories, see the [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) enumeration.</span></span> 

* <span data-ttu-id="d51c0-452">Sonraki karakterler kategorileri hiçbirini ilk karakter olarak olabilir ve aralık birleştirme işaretleri, ondalık sayılar, bağlayıcı noktalama işaretleri ve biçimlendirme kodları aralıksız işaretlerini de içerir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-452">Subsequent characters can be from any of the categories as the first character, and can also include non-spacing marks, spacing combining marks, decimal numbers, connector punctuations, and formatting codes.</span></span> 

<span data-ttu-id="d51c0-453">Tanımlayıcıları karşılaştırmak önce biçimlendirme veya kodları filtre ve tek bir karakter birden çok UTF-16 kodlu kod birimler tarafından temsil edilebilir bulunduğundan Unicode normalleştirme Form C tanımlayıcıları dönüştürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="d51c0-453">Before you compare identifiers, you should filter out formatting codes and convert the identifiers to Unicode Normalization Form C, because a single character can be represented by multiple UTF-16-encoded code units.</span></span> <span data-ttu-id="d51c0-454">Unicode normalleştirme Form C aynı kodu birimlerinde üretmek karakter sıralarının CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-454">Character sequences that produce the same code units in Unicode Normalization Form C are not CLS-compliant.</span></span> <span data-ttu-id="d51c0-455">Aşağıdaki örnek adlı bir özelliğini tanımlar `Å`ANGSTROM işareti (U + 212B) karakterinin oluşur ve ikinci bir özelliğe adlı `Å` LATIN büyük harf A ile HALKASI YUKARIDA (U + 00 C 5) karakterinin oluşur.</span><span class="sxs-lookup"><span data-stu-id="d51c0-455">The following example defines a property named `Å`, which consists of the character ANGSTROM SIGN (U+212B), and a second property named `Å` which consists of the character LATIN CAPITAL LETTER A WITH RING ABOVE (U+00C5).</span></span> <span data-ttu-id="d51c0-456">C# Derleyici kaynak kodu CLS uyumlu olmayan olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="d51c0-456">The C# compiler flags the source code as non-CLS-compliant.</span></span>

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

<span data-ttu-id="d51c0-457">Üye adlarının (örneğin, ad alanları bir ad alanı içindeki tür veya üye türünde bir derleme içinde) belirli bir kapsam içinde dışında aşırı yükleme aracılığıyla çözülür adları benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-457">Member names within a particular scope (such as the namespaces within an assembly, the types within a namespace, or the members within a type) must be unique except for names that are resolved through overloading.</span></span> <span data-ttu-id="d51c0-458">Bu gereksinim, farklı türde üye olduğu sürece, aynı adlara sahip bir kapsamı içinde birden çok üye sağlar ortak tür sistemi daha daha sıkı (örneğin, bir yöntem biridir ve bir alan biridir).</span><span class="sxs-lookup"><span data-stu-id="d51c0-458">This requirement is more stringent than that of the common type system, which allows multiple members within a scope to have identical names as long as they are different kinds of members (for example, one is a method and one is a field).</span></span> <span data-ttu-id="d51c0-459">Tür üyeleri için özel olarak:</span><span class="sxs-lookup"><span data-stu-id="d51c0-459">In particular, for type members:</span></span> 

* <span data-ttu-id="d51c0-460">Alanlar ve iç içe geçmiş türler adıyla ayırt edilir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-460">Fields and nested types are distinguished by name alone.</span></span> 

* <span data-ttu-id="d51c0-461">Yöntemler, özellikler ve aynı ada sahip olayları birden fazla yalnızca dönüş türüne göre farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-461">Methods, properties, and events that have the same name must differ by more than just return type.</span></span> 

<span data-ttu-id="d51c0-462">Aşağıdaki örnek üye adlarını kendi kapsamı içinde benzersiz olmalıdır gereksinim gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-462">The following example illustrates the requirement that member names must be unique within their scope.</span></span> <span data-ttu-id="d51c0-463">Adlı bir sınıf tanımlar `Converter` adlı dört üyeleri içeren `Conversion`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-463">It defines a class named `Converter` that includes four members named `Conversion`.</span></span> <span data-ttu-id="d51c0-464">Üç yöntemlerdir ve bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-464">Three are methods, and one is a property.</span></span> <span data-ttu-id="d51c0-465">İçeren yöntemi bir `Int64` parametresi benzersiz olarak adlandırılır, ancak iki yöntemle bir `Int32` parametresi değildir, çünkü dönüş değeri bir üyenin imza bir parçası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="d51c0-465">The method that includes an `Int64` parameter is uniquely named, but the two methods with an `Int32` parameter are not, because return value is not considered a part of a member's signature.</span></span> <span data-ttu-id="d51c0-466">`Conversion` Özelliği özelliklerin aşırı yüklenmiş yöntemler adıyla aynı olduğundan bu gereksinim ayrıca ihlal.</span><span class="sxs-lookup"><span data-stu-id="d51c0-466">The `Conversion` property also violates this requirement, because properties cannot have the same name as overloaded methods.</span></span> 

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

<span data-ttu-id="d51c0-467">Dilleri hedefleyen ortak dil çalışma zamanı da anahtar sözcükler ile çakıştığı tanımlayıcıları (gibi tür adları) başvuran için bazı mekanizma sağlamanız gerekir benzersiz anahtar sözcükler, tek tek dilleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-467">Individual languages include unique keywords, so languages that target the common language runtime must also provide some mechanism for referencing identifiers (such as type names) that coincide with keywords.</span></span> <span data-ttu-id="d51c0-468">Örneğin, `case` hem C# ve Visual Basic bir anahtar sözcüktür.</span><span class="sxs-lookup"><span data-stu-id="d51c0-468">For example, `case` is a keyword in both C# and Visual Basic.</span></span> <span data-ttu-id="d51c0-469">Ancak, aşağıdaki Visual Basic örnek adlı bir sınıf belirsizliğini ortadan kaldırmak mümkün `case` gelen `case` açma ve küme ayraçları kapatma kullanarak anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d51c0-469">However, the following Visual Basic example is able to disambiguate a class named `case` from the `case` keyword by using opening and closing braces.</span></span> <span data-ttu-id="d51c0-470">Aksi takdirde, örnek "Anahtar sözcüğü bir tanımlayıcı olarak geçerli değil" hata iletisi oluşturmak ve bu derlemek başarısız.</span><span class="sxs-lookup"><span data-stu-id="d51c0-470">Otherwise, the example would produce the error message, "Keyword is not valid as an identifier," and fail to compile.</span></span> 

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

<span data-ttu-id="d51c0-471">Aşağıdaki C# örnek örneği yapabiliyor `case` kullanarak sınıfı @ simgesinden dil anahtar sözcüğünü tanımlayıcıdan belirsizliğini ortadan kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="d51c0-471">The following C# example is able to instantiate the `case` class by using the @ symbol to disambiguate the identifier from the language keyword.</span></span> <span data-ttu-id="d51c0-472">Bu olmadan, C# Derleyici iki hata iletileri, "Tür bekleniyor" ve "geçersiz ifade terimi 'case'." görüntüler</span><span class="sxs-lookup"><span data-stu-id="d51c0-472">Without it, the C# compiler would display two error messages, "Type expected" and "Invalid expression term 'case'."</span></span> 

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

### <a name="type-conversion"></a><span data-ttu-id="d51c0-473">Tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="d51c0-473">Type conversion</span></span>

<span data-ttu-id="d51c0-474">Ortak dil belirtimi iki dönüşüm işleçleri tanımlar:</span><span class="sxs-lookup"><span data-stu-id="d51c0-474">The Common Language Specification defines two conversion operators:</span></span>

* <span data-ttu-id="d51c0-475">`op_Implicit`, hangi veri veya duyarlık kaybına neden değil dönüşümleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-475">`op_Implicit`, which is used for widening conversions that do not result in loss of data or precision.</span></span> <span data-ttu-id="d51c0-476">Örneğin, [ondalık](xref:System.Decimal) yapısı içeren bir aşırı yüklenmiş `op_Implicit` tam sayı türleri değerini dönüştürmek için işleci ve [Char](xref:System.Char) değerler `Decimal` değerleri.</span><span class="sxs-lookup"><span data-stu-id="d51c0-476">For example, the [Decimal](xref:System.Decimal) structure includes an overloaded `op_Implicit` operator to convert values of integral types and [Char](xref:System.Char) values to `Decimal` values.</span></span> 

* <span data-ttu-id="d51c0-477">`op_Explicit`, hangi daraltma (daha küçük bir aralık sahip bir değer için bir değer dönüştürülen) büyüklük veya duyarlık kaybına yol açabilir dönüşümleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-477">`op_Explicit`, which is used for narrowing conversions that can result in loss of magnitude (a value is converted to a value that has a smaller range) or precision.</span></span> <span data-ttu-id="d51c0-478">Örneğin, `Decimal` yapısı içeren bir aşırı yüklenmiş `op_Explicit` dönüştürmek için işleci [çift](xref:System.Double) ve [tek](xref:System.Single) değerler `Decimal` ve dönüştürmek için `Decimal` değerler tam sayı değerleri `Double`, `Single`, ve `Char`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-478">For example, the `Decimal` structure includes an overloaded `op_Explicit` operator to convert [Double](xref:System.Double) and [Single](xref:System.Single) values to `Decimal` and to convert `Decimal` values to integral values, `Double`, `Single`, and `Char`.</span></span> 

<span data-ttu-id="d51c0-479">Ancak, tüm diller İşleç aşırı yüklemesi ya da özel işleçleri tanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d51c0-479">However, not all languages support operator overloading or the definition of custom operators.</span></span> <span data-ttu-id="d51c0-480">Bu dönüşüm işleçleri uygulamak isterseniz dönüştürme gerçekleştirmek için alternatif bir yöntem sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-480">If you choose to implement these conversion operators, you should also provide an alternate way to perform the conversion.</span></span> <span data-ttu-id="d51c0-481">Sağlamanızı öneririz `From`Xxx ve `To`Xxx yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="d51c0-481">We recommend that you provide `From`Xxx and `To`Xxx methods.</span></span> 

<span data-ttu-id="d51c0-482">Aşağıdaki örnek, CLS uyumlu örtük ve açık dönüştürmeler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d51c0-482">The following example defines CLS-compliant implicit and explicit conversions.</span></span> <span data-ttu-id="d51c0-483">Oluşturduğu bir `UDouble` imzalı çift duyarlıklı, kayan noktalı sayıyı temsil eden sınıf.</span><span class="sxs-lookup"><span data-stu-id="d51c0-483">It creates a `UDouble` class that represents an signed double-precision, floating-point number.</span></span> <span data-ttu-id="d51c0-484">Örtük dönüşümler sağlayan `UDouble` için `Double` ve açık dönüştürmeler `UDouble` için `Single`, `Double` için `UDouble`, ve `Single` için `UDouble`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-484">It provides for implicit conversions from `UDouble` to `Double` and for explicit conversions from `UDouble` to `Single`, `Double` to `UDouble`, and `Single` to `UDouble`.</span></span> <span data-ttu-id="d51c0-485">Ayrıca tanımlayan bir `ToDouble` örtük dönüşüm işleci alternatif olarak yöntemi ve `ToSingle`, `FromDouble`, ve `FromSingle` açık dönüşüm işleçleri alternatifleri olarak yöntemler.</span><span class="sxs-lookup"><span data-stu-id="d51c0-485">It also defines a `ToDouble` method as an alternative to the implicit conversion operator and the `ToSingle`, `FromDouble`, and `FromSingle` methods as alternatives to the explicit conversion operators.</span></span> 

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

### <a name="arrays"></a><span data-ttu-id="d51c0-486">Diziler</span><span class="sxs-lookup"><span data-stu-id="d51c0-486">Arrays</span></span>

<span data-ttu-id="d51c0-487">CLS uyumlu diziler aşağıdaki kurallara uygun:</span><span class="sxs-lookup"><span data-stu-id="d51c0-487">CLS-compliant arrays conform to the following rules:</span></span> 

* <span data-ttu-id="d51c0-488">Bir dizinin tüm boyutları alt sınırı sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-488">All dimensions of an array must have a lower bound of zero.</span></span> <span data-ttu-id="d51c0-489">Aşağıdaki örnek, CLS uyumlu olmayan bir dizi alt sınır bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d51c0-489">The following example creates a non-CLS-compliant array with a lower bound of one.</span></span> <span data-ttu-id="d51c0-490">Unutmayın, varlığını rağmen [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği derleyici algılamazsa tarafından döndürülen dizi `Numbers.GetTenPrimes` yöntem CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-490">Note that, despite the presence of the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute, the compiler does not detect that the array returned by the `Numbers.GetTenPrimes` method is not CLS-compliant.</span></span> 

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

* <span data-ttu-id="d51c0-491">Tüm dizi öğeleri CLS uyumlu türleri oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-491">All array elements must consist of CLS-compliant types.</span></span> <span data-ttu-id="d51c0-492">Aşağıdaki örnek, CLS uyumlu olmayan dizileri döndürür iki yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d51c0-492">The following example defines two methods that return non-CLS-compliant arrays.</span></span> <span data-ttu-id="d51c0-493">İlk bir dizi döndürür [UInt32](xref:System.UInt32) değerleri.</span><span class="sxs-lookup"><span data-stu-id="d51c0-493">The first returns an array of [UInt32](xref:System.UInt32) values.</span></span> <span data-ttu-id="d51c0-494">İkinci döndürür bir [nesne](xref:System.Object) içeren bir dizi [Int32](xref:System.Int32) ve `UInt32` değerleri.</span><span class="sxs-lookup"><span data-stu-id="d51c0-494">The second returns an [Object](xref:System.Object) array that includes [Int32](xref:System.Int32) and `UInt32` values.</span></span> <span data-ttu-id="d51c0-495">İlk dizi uyumsuz olarak nedeniyle derleyici tanımlasa da, `UInt32` türü, başarısız ikinci dizi CLS uyumlu olmayan öğeler içeriyor tanımadığı.</span><span class="sxs-lookup"><span data-stu-id="d51c0-495">Although the compiler identifies the first array as non-compliant because of its `UInt32` type, it fails to recognize that the second array includes non-CLS-compliant elements.</span></span> 

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

* <span data-ttu-id="d51c0-496">Dizi parametrelerine sahip yöntemleri için aşırı yükleme çözünürlüğü diziler oldukları dayanarak açık nedeni olduğunu ve bunların öğe türü bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="d51c0-496">Overload resolution for methods that have array parameters is based on the fact that they are arrays and on their element type.</span></span> <span data-ttu-id="d51c0-497">Bu nedenle, aşırı yüklenmiş bir aşağıdaki tanımını `GetSquares` yöntem CLS uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="d51c0-497">For this reason, the following definition of an overloaded `GetSquares` method is CLS-compliant.</span></span> 

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

### <a name="interfaces"></a><span data-ttu-id="d51c0-498">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="d51c0-498">Interfaces</span></span>

<span data-ttu-id="d51c0-499">CLS uyumlu arabirimleri özellikleri, olayları ve sanal yöntemler (uygulaması yöntemleriyle) tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d51c0-499">CLS-compliant interfaces can define properties, events, and virtual methods (methods with no implementation).</span></span> <span data-ttu-id="d51c0-500">CLS uyumlu bir arabirim aşağıdakilerden herhangi birini içeremez:</span><span class="sxs-lookup"><span data-stu-id="d51c0-500">A CLS-compliant interface cannot have any of the following:</span></span> 

* <span data-ttu-id="d51c0-501">Statik yöntemler veya statik alanları.</span><span class="sxs-lookup"><span data-stu-id="d51c0-501">Static methods or static fields.</span></span> <span data-ttu-id="d51c0-502">Bir arabirim, statik bir üyenin tanımlarsanız, C# Derleyici generatse derleyici hataları.</span><span class="sxs-lookup"><span data-stu-id="d51c0-502">The C# compiler generatse compiler errors if you define a static member in an interface.</span></span> 

* <span data-ttu-id="d51c0-503">Alanlar.</span><span class="sxs-lookup"><span data-stu-id="d51c0-503">Fields.</span></span> <span data-ttu-id="d51c0-504">Bir alan bir arabirim tanımlarsanız, C# acompiler derleyici hataları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d51c0-504">The C# acompiler generates compiler errors if you define a field in an interface.</span></span>

* <span data-ttu-id="d51c0-505">CLS uyumlu olmayan yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="d51c0-505">Methods that are not CLS-compliant.</span></span> <span data-ttu-id="d51c0-506">Örneğin, aşağıdaki arabirim tanımı bir yöntem içerir `INumber.GetUnsigned`, yani olarak-CLS uyumlu olmayan olarak işaretlenmiş.</span><span class="sxs-lookup"><span data-stu-id="d51c0-506">For example, the following interface definition includes a method, `INumber.GetUnsigned`, that is marked as non-CLS-compliant.</span></span> <span data-ttu-id="d51c0-507">Bu örnek derleyici uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d51c0-507">This example generates a compiler warning.</span></span> 

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

  <span data-ttu-id="d51c0-508">Bu kural nedeniyle CLS uyumlu türleri CLS uyumlu olmayan üyeler uygulamak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-508">Because of this rule, CLS-compliant types are not required to implement non-CLS-compliant members.</span></span> <span data-ttu-id="d51c0-509">CLS dışı uyumlu arabirimini uygulayan bir sınıf CLS uyumlu bir çerçeve kullanıma, CLS uyumlu olmayan tüm üyelerin somut uygulamaları da sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-509">If a CLS-compliant framework does expose a class that implements a non-CLS compliant interface, it should also provide concrete implementations of all non-CLS-compliant members.</span></span> 

<span data-ttu-id="d51c0-510">CLS uyumlu dil derleyicileri aynı ad ve imza birden çok arabirimlerde sahip üyeler ayrı uygulamalarını için bir sınıf de izin vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-510">CLS-compliant language compilers must also allow a class to provide separate implementations of members that have the same name and signature in multiple interfaces.</span></span> <span data-ttu-id="d51c0-511">C# aynı adlı yöntemlerin farklı uygulamaları sağlamak için açık arabirim uygulamaları destekler.</span><span class="sxs-lookup"><span data-stu-id="d51c0-511">C# supports explicit interface implementations to provide different implementations of identically named methods.</span></span> <span data-ttu-id="d51c0-512">Aşağıdaki örnekte, tanımlayarak bu senaryo gösterilmektedir bir `Temperature` uygulayan sınıf `ICelsius` ve `IFahrenheit` arabirimleri açık arabirim uygulamaları olarak.</span><span class="sxs-lookup"><span data-stu-id="d51c0-512">The following example illustrates this scenario by defining a `Temperature` class that implements the `ICelsius` and `IFahrenheit` interfaces as explicit interface implementations.</span></span> 

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

### <a name="enumerations"></a><span data-ttu-id="d51c0-513">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="d51c0-513">Enumerations</span></span>

<span data-ttu-id="d51c0-514">CLS uyumlu numaralandırmalar bu kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="d51c0-514">CLS-compliant enumerations must follow these rules:</span></span> 

* <span data-ttu-id="d51c0-515">Temel alınan numaralandırması iç CLS uyumlu Tamsayı türünde olmalıdır ([bayt](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), veya [Int64](xref:System.Int64)).</span><span class="sxs-lookup"><span data-stu-id="d51c0-515">The underlying type of the enumeration must be an intrinsic CLS-compliant integer ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), or [Int64](xref:System.Int64)).</span></span> <span data-ttu-id="d51c0-516">Örneğin, temel alınan türü olan bir numaralandırma tanımlamak aşağıdaki kodu çalışır [UInt32](xref:System.UInt32) ve derleyici uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d51c0-516">For example, the following code tries to define an enumeration whose underlying type is [UInt32](xref:System.UInt32) and generates a compiler warning.</span></span> 

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

* <span data-ttu-id="d51c0-517">Bir numaralandırma türü adlı tek örnek alanı olmalıdır `Value__` ile işaretlenmiş `FieldAttributes.RTSpecialName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d51c0-517">An enumeration type must have a single instance field named `Value__` that is marked with the `FieldAttributes.RTSpecialName` attribute.</span></span> <span data-ttu-id="d51c0-518">Bu alan değeri örtük olarak başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="d51c0-518">This enables you to reference the field value implicitly.</span></span> 

* <span data-ttu-id="d51c0-519">Numaralandırma, türü numaralandırma türüyle eşleşen değişmez değer statik alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-519">An enumeration includes literal static fields whose types match the type of the enumeration itself.</span></span> <span data-ttu-id="d51c0-520">Örneğin, tanımladığınız bir `State` değerlerle numaralandırma `State.On` ve `State.Off`, `State.On` ve `State.Off` türü olan iki değişmez değer statik alanları `State`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-520">For example, if you define a `State` enumeration with values of `State.On` and `State.Off`, `State.On` and `State.Off` are both literal static fields whose type is `State`.</span></span> 

* <span data-ttu-id="d51c0-521">Numaralandırmalar iki tür vardır:</span><span class="sxs-lookup"><span data-stu-id="d51c0-521">There are two kinds of enumerations:</span></span> 
    
    * <span data-ttu-id="d51c0-522">Birbirini dışlayan kümesini temsil eden numaralandırma adlı tamsayı değerleri.</span><span class="sxs-lookup"><span data-stu-id="d51c0-522">An enumeration that represents a set of mutually exclusive, named integer values.</span></span> <span data-ttu-id="d51c0-523">Bu numaralandırma türü yokluğu tarafından gösterilen [System.FlagsAttribute](xref:System.FlagsAttribute) özel öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d51c0-523">This type of enumeration is indicated by the absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>
    
    * <span data-ttu-id="d51c0-524">Adsız bir değer üretmek için birleştirebilirsiniz bit bayrakları kümesini temsil eden bir numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="d51c0-524">An enumeration that represents a set of bit flags that can combine to generate an unnamed value.</span></span> <span data-ttu-id="d51c0-525">Bu numaralandırma türü varlığını tarafından gösterilen [System.FlagsAttribute](xref:System.FlagsAttribute) özel öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d51c0-525">This type of enumeration is indicated by the presence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>
    
 <span data-ttu-id="d51c0-526">Daha fazla bilgi için belgelerine bakın [Enum](xref:System.Enum) yapısı.</span><span class="sxs-lookup"><span data-stu-id="d51c0-526">For more information, see the documentation for the [Enum](xref:System.Enum) structure.</span></span> 

* <span data-ttu-id="d51c0-527">Numaralandırma değeri, belirtilen değer aralığı için sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-527">The value of an enumeration is not limited to the range of its specified values.</span></span> <span data-ttu-id="d51c0-528">Diğer bir deyişle, numaralandırma değerlerinin aralığını temel değerini aralığıdır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-528">In other words, the range of values in an enumeration is the range of its underlying value.</span></span> <span data-ttu-id="d51c0-529">Kullanabileceğiniz `Enum.IsDefined` belirtilen bir değeri bir numaralandırma üyesi olup olmadığının yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d51c0-529">You can use the `Enum.IsDefined` method to determine whether a specified value is a member of an enumeration.</span></span> 

### <a name="type-members-in-general"></a><span data-ttu-id="d51c0-530">Genel üyeleri yazın</span><span class="sxs-lookup"><span data-stu-id="d51c0-530">Type members in general</span></span>

<span data-ttu-id="d51c0-531">Ortak dil belirtimi, tüm alanları ve belirli bir sınıfın bir üyesi olarak erişilecek yöntemleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-531">The Common Language Specification requires all fields and methods to be accessed as members of a particular class.</span></span> <span data-ttu-id="d51c0-532">Bu nedenle, genel statik alanları ve yöntemleri (diğer bir deyişle, statik alanları veya dışında bir türü tanımlanmadı yöntemleri) CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-532">Therefore, global static fields and methods (that is, static fields or methods that are defined apart from a type) are not CLS-compliant.</span></span> <span data-ttu-id="d51c0-533">Genel alan veya yöntem kaynak kodunuzda eklemeye çalışırsanız, C# Derleyici derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d51c0-533">If you try to include a global field or method in your source code, the C# compiler generates a compiler error.</span></span> 

<span data-ttu-id="d51c0-534">Yalnızca standart çağırma yönetilen ortak dil belirtimi destekler.</span><span class="sxs-lookup"><span data-stu-id="d51c0-534">The Common Language Specification supports only the standard managed calling convention.</span></span> <span data-ttu-id="d51c0-535">Yönetilmeyen çağırma kurallarını desteklemez ve değişken bağımsız değişken listeleri yöntemleriyle işaretlenmiş `varargs` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d51c0-535">It doesn't support unmanaged calling conventions and methods with variable argument lists marked with the `varargs` keyword.</span></span> <span data-ttu-id="d51c0-536">Standart yönetilen çağırma kuralı ile uyumlu olan değişken bağımsız değişken listeleri için kullanmak [ParamArrayAttribute](xref:System.ParamArrayAttribute) özniteliği ya da tek tek dil uygulaması gibi `params` C# anahtar sözcüğü ve `ParamArray` Visual Basic anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d51c0-536">For variable argument lists that are compatible with the standard managed calling convention, use the [ParamArrayAttribute](xref:System.ParamArrayAttribute) attribute or the individual language's implementation, such as the `params` keyword in C# and the `ParamArray` keyword in Visual Basic.</span></span> 

### <a name="member-accessibility"></a><span data-ttu-id="d51c0-537">Üye erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="d51c0-537">Member accessibility</span></span>

<span data-ttu-id="d51c0-538">Devralınmış bir üyeyi geçersiz kılma bu üyede erişilebilirliğini değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d51c0-538">Overriding an inherited member cannot change the accessibility of that member.</span></span> <span data-ttu-id="d51c0-539">Örneğin, bir taban sınıf ortak yönteminde, türetilmiş bir sınıf içinde özel bir yöntem tarafından değiştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="d51c0-539">For example, a public method in a base class cannot be overridden by a private method in a derived class.</span></span> <span data-ttu-id="d51c0-540">Bir istisna vardır: bir `protected internal` (C# ' ta) veya `Protected Friend` (Visual Basic'te) farklı bir derlemedeki bir türe göre geçersiz bir derleme üyesi.</span><span class="sxs-lookup"><span data-stu-id="d51c0-540">There is one exception: a `protected internal` (in C#) or `Protected Friend` (in Visual Basic) member in one assembly that is overridden by a type in a different assembly.</span></span>  <span data-ttu-id="d51c0-541">Bu durumda, geçersiz kılma erişilebilirliğini olduğu `Protected`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-541">In that case, the accessibility of the override is `Protected`.</span></span> 

<span data-ttu-id="d51c0-542">Aşağıdaki örnek hata gösterilmektedir oluşturulan [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği `true`, ve `Person`, hangi bir sınıfın türetildiği `Animal`, değiştirmeye çalışırsa erişilebilirliğini `Species` ortak özelliğinden özel.</span><span class="sxs-lookup"><span data-stu-id="d51c0-542">The following example illustrates the error that is generated when the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is set to `true`, and `Person`, which is a class derived from `Animal`, tries to change the accessibility of the `Species` property from public to private.</span></span> <span data-ttu-id="d51c0-543">Kendi erişilebilirlik ortak olarak değiştirilirse örnek başarıyla derler.</span><span class="sxs-lookup"><span data-stu-id="d51c0-543">The example compiles successfully if its accessibility is changed to public.</span></span> 

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

<span data-ttu-id="d51c0-544">Bu üye erişilebilir olduğunda imza türlerinde üyenin erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-544">Types in the signature of a member must be accessible whenever that member is accessible.</span></span> <span data-ttu-id="d51c0-545">Örneğin, bu ortak üyesi özel, korumalı veya dahili türü olan bir parametre içeremez anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-545">For example, this means that a public member cannot include a parameter whose type is private, protected, or internal.</span></span> <span data-ttu-id="d51c0-546">Aşağıdaki örnek sonuçları derleyici hatası gösterilmektedir, bir `StringWrapper` sınıfı oluşturucusu kullanıma sunan bir iç `StringOperationType` bir dize değeri nasıl alınmalı belirler numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="d51c0-546">The following example illustrates the compiler error that results when a `StringWrapper` class constructor exposes an internal `StringOperationType` enumeration value that determines how a string value should be wrapped.</span></span> 

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

### <a name="generic-types-and-members"></a><span data-ttu-id="d51c0-547">Genel türler ve üyeleri</span><span class="sxs-lookup"><span data-stu-id="d51c0-547">Generic types and members</span></span>

<span data-ttu-id="d51c0-548">İç içe geçmiş türler, kendilerini kapsayan türle her zaman en az sayıda genel parametrelere sahip.</span><span class="sxs-lookup"><span data-stu-id="d51c0-548">Nested types always have at least as many generic parameters as their enclosing type.</span></span> <span data-ttu-id="d51c0-549">Bunlar, kendilerini kapsayan türle genel parametreler konuma göre karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-549">These correspond by position to the generic parameters in the enclosing type.</span></span> <span data-ttu-id="d51c0-550">Genel tür yeni genel parametreler de içerir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-550">The generic type can also include new generic parameters.</span></span> 

<span data-ttu-id="d51c0-551">Genel tür parametreleri içeren bir türde ve iç içe geçmiş türler arasındaki ilişki tek tek dilleri sözdizimi tarafından gizlenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-551">The relationship between the generic type parameters of a containing type and its nested types may be hidden by the syntax of individual languages.</span></span> <span data-ttu-id="d51c0-552">Aşağıdaki örnekte, genel bir tür `Outer<T>` iki iç içe geçmiş sınıflar içeren `Inner1A` ve `Inner1B<U>`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-552">In the following example, a generic type `Outer<T>` contains two nested classes, `Inner1A` and `Inner1B<U>`.</span></span> <span data-ttu-id="d51c0-553">Çağrıları `ToString` her sınıfının devraldığı yöntemi `Object.ToString`, her iç içe geçmiş sınıf kapsayan sınıfı tür parametrelerini içerdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-553">The calls to the `ToString` method, which each class inherits from `Object.ToString`, show that each nested class includes the type parameters of its containing class.</span></span> 

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

<span data-ttu-id="d51c0-554">Genel tür adları biçiminde kodlanmış *adı*'*n*, burada *adı* tür adı *\`* bir karakter değişmez değeri değil ve *n* türünde bildirilen parametrelerin sayısı veya genel iç içe geçmiş için türleri, yeni sunulan türü parametre sayısı.</span><span class="sxs-lookup"><span data-stu-id="d51c0-554">Generic type names are encoded in the form *name*'*n*, where *name* is the type name, *\`* is a character literal, and *n* is the number of parameters declared on the type, or, for nested generic types, the number of newly introduced type parameters.</span></span> <span data-ttu-id="d51c0-555">Bu genel tür adları CLS uyumlu bir Kitaplığı'nda genel türler erişmek için yansıma kullanan geliştiriciler öncelikle ilgisini kodlamadır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-555">This encoding of generic type names is primarily of interest to developers who use reflection to access CLS-complaint generic types in a library.</span></span> 

<span data-ttu-id="d51c0-556">Bir genel kısıtlamalar uyguladıysanız kısıtlamaları da CLS ile uyumlu olması gerektiği kullanılan türleri yazın.</span><span class="sxs-lookup"><span data-stu-id="d51c0-556">If constraints are applied to a generic type, any types used as constraints must also be CLS-compliant.</span></span> <span data-ttu-id="d51c0-557">Aşağıdaki örnek adlı bir sınıf tanımlar `BaseClass` yani değil CLS ile uyumlu ve adlı genel bir sınıf `BaseCollection` , tür parametresi öğesinden türetilmelidir `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-557">The following example defines a class named `BaseClass` that is not CLS-compliant and a generic class named `BaseCollection` whose type parameter must derive from `BaseClass`.</span></span> <span data-ttu-id="d51c0-558">Ancak çünkü `BaseClass` CLS uyumlu olmayan bir uyarı derleyicisi yayar.</span><span class="sxs-lookup"><span data-stu-id="d51c0-558">But because `BaseClass` is not CLS-compliant, the compiler emits a warning.</span></span> 

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

<span data-ttu-id="d51c0-559">Genel bir tür genel bir temel türden türetilmiş, böylece temel türü kısıtlamaları da karşılanır garanti edebilir kısıtlamalar redeclare gerekir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-559">If a generic type is derived from a generic base type, it must redeclare any constraints so that it can guarantee that constraints on the base type are also satisfied.</span></span> <span data-ttu-id="d51c0-560">Aşağıdaki örnek tanımlayan bir `Number<T>` herhangi bir sayısal tür temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-560">The following example defines a `Number<T>` that can represent any numeric type.</span></span> <span data-ttu-id="d51c0-561">Ayrıca tanımlayan bir `FloatingPoint<T>` kayan temsil eden sınıf noktası değeri.</span><span class="sxs-lookup"><span data-stu-id="d51c0-561">It also defines a `FloatingPoint<T>` class that represents a floating point value.</span></span> <span data-ttu-id="d51c0-562">Bu kısıtlama geçerli değildir çünkü ancak, Kaynak Kodu derlemek başarısız `Number<T>` (T değeri türü olması gerekir) için `FloatingPoint<T>`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-562">However, the source code fails to compile, because it does not apply the constraint on `Number<T>` (that T must be a value type) to `FloatingPoint<T>`.</span></span>

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
// The attempt to comple the example displays the following output:
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
' The attempt to comple the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'    
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

<span data-ttu-id="d51c0-563">Kısıtlama eklenirse, örnek başarıyla derlenen `FloatingPoint<T>` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d51c0-563">The example compiles successfully if the constraint is added to the `FloatingPoint<T>` class.</span></span>

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

<span data-ttu-id="d51c0-564">Ortak dil belirtimi, iç içe geçmiş türler için koruyucu örneklemesi başına modeli uygular ve korumalı üyeler.</span><span class="sxs-lookup"><span data-stu-id="d51c0-564">The Common Language Specification imposes a conservative per-instantiation model for nested types and protected members.</span></span> <span data-ttu-id="d51c0-565">Açık genel türler alanları veya iç içe geçmiş, korumalı bir genel türü belirli bir örnek oluşturma içeren imzaları üyeleriyle gösteremez.</span><span class="sxs-lookup"><span data-stu-id="d51c0-565">Open generic types cannot expose fields or members with signatures that contain a specific instantiation of a nested, protected generic type.</span></span> <span data-ttu-id="d51c0-566">Belirli bir örnek oluşturma genel temel sınıf veya arabirim genişletmek olmayan genel türleri, alanlar veya iç içe geçmiş, korumalı bir genel türü farklı bir örnek oluşturma içeren imzaları üyeleriyle gösteremez.</span><span class="sxs-lookup"><span data-stu-id="d51c0-566">Non-generic types that extend a specific instantiation of a generic base class or interface cannot expose fields or members with signatures that contain a different instantiation of a nested, protected generic type.</span></span>

<span data-ttu-id="d51c0-567">Aşağıdaki örnek, genel bir tür tanımlar `C1<T>`ve korumalı bir sınıf `C1<T>.N`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-567">The following example defines a generic type, `C1<T>`, and a protected class, `C1<T>.N`.</span></span> <span data-ttu-id="d51c0-568">`C1<T>` iki yöntemi vardır `M1` ve `M2`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-568">`C1<T>` has two methods, `M1` and `M2`.</span></span> <span data-ttu-id="d51c0-569">Ancak, `M1` döndürmeye çalışır CLS uyumlu olmadığından bir `C1<int>.N` nesnesinin `C1<T>`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-569">However, `M1` is not CLS-compliant because it tries to return a `C1<int>.N` object from `C1<T>`.</span></span> <span data-ttu-id="d51c0-570">İkinci sınıfı `C2`, türetildiği `C1<long>`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-570">A second class, `C2`, is derived from `C1<long>`.</span></span> <span data-ttu-id="d51c0-571">İki yöntemi vardır `M3` ve `M4`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-571">It has two methods, `M3` and `M4`.</span></span> <span data-ttu-id="d51c0-572">`M3` döndürmeye çalışır CLS uyumlu olmadığından bir `C1<int>.N` öğesinin bir alt nesne `C1<long>`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-572">`M3` is not CLS-compliant because it tries to return a `C1<int>.N` object from a subclass of `C1<long>`.</span></span> <span data-ttu-id="d51c0-573">Dil derleyicileri daha kısıtlayıcı olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d51c0-573">Note that language compilers can be even more restrictive.</span></span> <span data-ttu-id="d51c0-574">Derlemeye çalıştığında bu örnekte, Visual Basic hata görüntüler. `M4`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-574">In this example, Visual Basic displays an error when it tries to compile `M4`.</span></span> 

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

### <a name="constructors"></a><span data-ttu-id="d51c0-575">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="d51c0-575">Constructors</span></span>

<span data-ttu-id="d51c0-576">CLS uyumlu sınıfları ve yapıları oluşturucular bu kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="d51c0-576">Constructors in CLS-compliant classes and structures must follow these rules:</span></span> 

* <span data-ttu-id="d51c0-577">Devralınan örnek veri erişim izni vermeden önce türetilmiş bir sınıf oluşturucusunun olduğu temel sınıfın örneği oluşturucusu çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-577">A constructor of a derived class must call the instance constructor of its base class before it accesses inherited instance data.</span></span> <span data-ttu-id="d51c0-578">Taban sınıf oluşturucular kendi türetilmiş sınıflar tarafından devralınır değil due için bu gereksinim olabilir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-578">This requirement is due to the fact that base class constructors are not inherited by their derived classes.</span></span> <span data-ttu-id="d51c0-579">Bu kural doğrudan devralma desteklemeyen yapıları için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-579">This rule does not apply to structures, which do not support direct inheritance.</span></span> 

  <span data-ttu-id="d51c0-580">Genellikle, bu kural aşağıdaki örnekte gösterildiği gibi CLS uyumluluğu bağımsız olarak derleyicileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d51c0-580">Typically, compilers enforce this rule independently of CLS compliance, as the following example shows.</span></span> <span data-ttu-id="d51c0-581">Oluşturduğu bir `Doctor` türetilmiş sınıf bir `Person` sınıfı, ancak `Doctor` sınıfı başarısız çağırmak `Person` devralınan örneği alanları başlatmak için sınıf oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="d51c0-581">It creates a `Doctor` class that is derived from a `Person` class, but the `Doctor` class fails to call the `Person` class constructor to initialize inherited instance fields.</span></span> 

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
    
* <span data-ttu-id="d51c0-582">Bir nesne oluşturucusu, nesneyi oluşturmak için dışında çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="d51c0-582">An object constructor cannot be called except to create an object.</span></span> <span data-ttu-id="d51c0-583">Ayrıca, bir nesne iki kez başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="d51c0-583">In addition, an object cannot be initialized twice.</span></span> <span data-ttu-id="d51c0-584">Örneğin, bunun anlamı `Object.MemberwiseClone` oluşturucular çağırmalısınız değil.</span><span class="sxs-lookup"><span data-stu-id="d51c0-584">For example, this means that `Object.MemberwiseClone` must not call constructors.</span></span>  

### <a name="properties"></a><span data-ttu-id="d51c0-585">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-585">Properties</span></span>

<span data-ttu-id="d51c0-586">CLS uyumlu türleri özelliklerinde bu kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="d51c0-586">Properties in CLS-compliant types must follow these rules:</span></span>

* <span data-ttu-id="d51c0-587">Özellik ayarlayıcı, bir alıcı ya da her ikisini de olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-587">A property must have a setter, a getter, or both.</span></span> <span data-ttu-id="d51c0-588">Derlemede, bu özel yöntemleri, ayrı yöntemleri olarak görünürler yani uygulanır (alıcı adlı `get` \_ *propertyname* ve kurucu `set*\_*propertyname*) marked as `SpecialName' ın derlemenin meta veriler.</span><span class="sxs-lookup"><span data-stu-id="d51c0-588">In an assembly, these are implemented as special methods, which means that they will appear as separate methods (the getter is named `get`\_*propertyname* and the setter is `set*\_*propertyname*) marked as `SpecialName\` in the assembly's metadata.</span></span> <span data-ttu-id="d51c0-589">Bu kural uygulamak için otomatik olarak gerek kalmadan C# Derleyici zorlar [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d51c0-589">The C# compiler enforces this rule automatically without the need to apply the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute.</span></span> 

* <span data-ttu-id="d51c0-590">Bir özelliğin özellik alıcısı dönüş türü ve kurucu son bağımsız değişkeni türüdür.</span><span class="sxs-lookup"><span data-stu-id="d51c0-590">A property's type is the return type of the property getter and the last argument of the setter.</span></span> <span data-ttu-id="d51c0-591">Bu tür CLS uyumlu olması gerekir ve bağımsız değişkenler atanamaz özelliğine başvuruya göre (diğer bir deyişle, bunlar yönetilen işaretçileri olamaz).</span><span class="sxs-lookup"><span data-stu-id="d51c0-591">These types must be CLS compliant, and arguments cannot be assigned to the property by reference (that is, they cannot be managed pointers).</span></span> 

* <span data-ttu-id="d51c0-592">Bir özelliği hem alıcı hem de ayarlayıcı varsa, bunlar hem de sanal olmalıdır hem statik ya da her iki örneği.</span><span class="sxs-lookup"><span data-stu-id="d51c0-592">If a property has both a getter and a setter, they must both be virtual, both static, or both instance.</span></span> <span data-ttu-id="d51c0-593">C# derleyici otomatik olarak bu kural özellik tanımı sözdizimi aracılığıyla zorlar.</span><span class="sxs-lookup"><span data-stu-id="d51c0-593">The C# compiler automatically enforces this rule through property definition syntax.</span></span> 

### <a name="events"></a><span data-ttu-id="d51c0-594">Olaylar</span><span class="sxs-lookup"><span data-stu-id="d51c0-594">Events</span></span>

<span data-ttu-id="d51c0-595">Bir olay adını ve türünü tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-595">An event is defined by its name and its type.</span></span> <span data-ttu-id="d51c0-596">Olay türü olay göstermek için kullanılan bir temsilcisidir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-596">The event type is a delegate that is used to indicate the event.</span></span> <span data-ttu-id="d51c0-597">Örneğin, `DbConnection.StateChange` olay türüdür `StateChangeEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-597">For example, the `DbConnection.StateChange` event is of type `StateChangeEventHandler`.</span></span> <span data-ttu-id="d51c0-598">Olayın kendisi, ek olarak, üç yöntem olay adına göre adlarıyla olayın uygulamasını sağlamak ve olarak işaretlenmiş `SpecialName` derlemenin meta verilerini de:</span><span class="sxs-lookup"><span data-stu-id="d51c0-598">In addition to the event itself, three methods with names based on the event name provide the event's implementation and are marked as `SpecialName` in the assembly's metadata:</span></span> 

* <span data-ttu-id="d51c0-599">Adlı bir olay işleyicisi eklemek için bir yöntem `add`_*EventName*.</span><span class="sxs-lookup"><span data-stu-id="d51c0-599">A method for adding an event handler, named `add`_*EventName*.</span></span> <span data-ttu-id="d51c0-600">Örneğin, abonelik için olay yöntemi `DbConnection.StateChange` olay adlandırılan `add_StateChange`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-600">For example, the event subscription method for the `DbConnection.StateChange` event is named `add_StateChange`.</span></span> 

* <span data-ttu-id="d51c0-601">Adlı bir olay işleyicisi kaldırmak için bir yöntem `remove`_*EventName*.</span><span class="sxs-lookup"><span data-stu-id="d51c0-601">A method for removing an event handler, named `remove`_*EventName*.</span></span> <span data-ttu-id="d51c0-602">Örneğin, temizleme yöntemi için `DbConnection.StateChange` olay adlandırılan `remove_StateChange`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-602">For example, the removal method for the `DbConnection.StateChange` event is named `remove_StateChange`.</span></span>

* <span data-ttu-id="d51c0-603">Olay oluştu, belirten yöntemi adlı `raise`_*EventName*.</span><span class="sxs-lookup"><span data-stu-id="d51c0-603">A method for indicating that the event has occurred, named `raise`_*EventName*.</span></span> 

> [!NOTE]
> <span data-ttu-id="d51c0-604">Ortak dil belirtimi'nın kuralları olayları ile ilgili çoğu dil derleyicileri tarafından uygulanan ve Bileşen geliştiriciler için saydamdır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-604">Most of the Common Language Specification's rules regarding events are implemented by language compilers and are transparent to component developers.</span></span> 

<span data-ttu-id="d51c0-605">Eklemek için yöntemleri, kaldırma ve olayı tetiklenmeden aynı erişilebilirlik olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-605">The methods for adding, removing, and raising the event must have the same accessibility.</span></span> <span data-ttu-id="d51c0-606">Bunlar ayrıca tüm statik olmalıdır örneği veya sanal.</span><span class="sxs-lookup"><span data-stu-id="d51c0-606">They must also all be static, instance, or virtual.</span></span> <span data-ttu-id="d51c0-607">İçin yöntemler ekleme ve kaldırma bir olay türü olay temsilci türü olan bir parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-607">The methods for adding and removing an event have one parameter whose type is the event delegate type.</span></span> <span data-ttu-id="d51c0-608">Add ve remove yöntemlerini hem de mevcut olmalıdır veya her ikisi de yok.</span><span class="sxs-lookup"><span data-stu-id="d51c0-608">The add and remove methods must both be present or both be absent.</span></span> 

<span data-ttu-id="d51c0-609">Aşağıdaki örnek adlı CLS uyumlu bir sınıfı tanımlar `Temperature` olayını bir `TemperatureChanged` iki okumalar arasında sıcaklık değişikliği değerine eşit veya eşik değeri, olay.</span><span class="sxs-lookup"><span data-stu-id="d51c0-609">The following example defines a CLS-compliant class named `Temperature` that raises a `TemperatureChanged` event if the change in temperature between two readings equals or exceeds a threshold value.</span></span> <span data-ttu-id="d51c0-610">`Temperature` Sınıfı açıkça tanımlayan bir `raise_TemperatureChanged` yöntemi olan olay işleyicileri seçmeli olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d51c0-610">The `Temperature` class explicitly defines a `raise_TemperatureChanged` method so that it can selectively execute event handlers.</span></span>

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

### <a name="overloads"></a><span data-ttu-id="d51c0-611">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="d51c0-611">Overloads</span></span>

<span data-ttu-id="d51c0-612">Ortak dil belirtimi aşırı yüklenmiş üyeler aşağıdaki gereksinimleri getirir:</span><span class="sxs-lookup"><span data-stu-id="d51c0-612">The Common Language Specification imposes the following requirements on overloaded members:</span></span> 

* <span data-ttu-id="d51c0-613">Üyeleri parametrelerin sayısı ve herhangi bir parametre türünü temel alan aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="d51c0-613">Members can be overloaded based on the number of parameters and the type of any parameter.</span></span> <span data-ttu-id="d51c0-614">Çağırma kuralı, dönüş türü, özel değiştiricileri yöntemi veya onun parametresi uygulanır ve parametreleri değere veya başvuruya göre geçirilir dikkate alınmaz zaman overloads arasında ayrım yapma.</span><span class="sxs-lookup"><span data-stu-id="d51c0-614">Calling convention, return type, custom modifiers applied to the method or its parameter, and whether parameters are passed by value or by reference are not considered when differentiating between overloads.</span></span> <span data-ttu-id="d51c0-615">Adları gereksinim bir kapsam içinde benzersiz olmalıdır, bir örnek için kodu görmek [adlandırma kuralları](#naming-conventions) bölümü.</span><span class="sxs-lookup"><span data-stu-id="d51c0-615">For an example, see the code for the requirement that names must be unique within a scope in the [Naming conventions](#naming-conventions) section.</span></span> 

* <span data-ttu-id="d51c0-616">Yalnızca özelliklerini ve yöntemlerini aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="d51c0-616">Only properties and methods can be overloaded.</span></span> <span data-ttu-id="d51c0-617">Alanlar ve olayları aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="d51c0-617">Fields and events cannot be overloaded.</span></span> 

* <span data-ttu-id="d51c0-618">Genel yöntemler genel parametrelerini sayısına göre aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="d51c0-618">Generic methods can be overloaded based on the number of their generic parameters.</span></span> 

> [!NOTE]
><span data-ttu-id="d51c0-619">`op_Explicit` Ve `op_Implicit` işleçleri aşırı yükleme çözünürlüğü için bir yöntem imzası parçası değeri dikkate alınmaz döndüren kural istisnalar mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="d51c0-619">The `op_Explicit` and `op_Implicit` operators are exceptions to the rule that return value is not considered part of a method signature for overload resolution.</span></span> <span data-ttu-id="d51c0-620">Bu iki işleç parametrelerini ve dönüş değerlerine göre aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="d51c0-620">These two operators can be overloaded based on both their parameters and their return value.</span></span> 

### <a name="exceptions"></a><span data-ttu-id="d51c0-621">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="d51c0-621">Exceptions</span></span>

<span data-ttu-id="d51c0-622">Özel durum nesneleri öğesinden türetilmelidir [System.Exception](xref:System.Exception) veya başka bir türden türetilmiş `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-622">Exception objects must derive from [System.Exception](xref:System.Exception) or from another type derived from `System.Exception`.</span></span> <span data-ttu-id="d51c0-623">Aşağıdaki örnek adlı özel bir sınıf sonuçlara derleyici hatası gösterilmektedir `ErrorClass` özel durum işleme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-623">The following example illustrates the compiler error that results when a custom class named `ErrorClass` is used for exception handling.</span></span>

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

<span data-ttu-id="d51c0-624">Bu hatayı düzeltmek için `ErrorClass` sınıfı öğesinden devralmalıdır `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-624">To correct this error, the `ErrorClass` class must inherit from `System.Exception`.</span></span> <span data-ttu-id="d51c0-625">Ayrıca, ileti özelliği geçersiz kılınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-625">In addition, the Message property must be overridden.</span></span> <span data-ttu-id="d51c0-626">Aşağıdaki örnek tanımlamak için bu hataları düzeltir bir `ErrorClass` CLS uyumlu sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d51c0-626">The following example corrects these errors to define an `ErrorClass` class that is CLS-compliant.</span></span>  

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

### <a name="attributes"></a><span data-ttu-id="d51c0-627">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d51c0-627">Attributes</span></span>

<span data-ttu-id="d51c0-628">In.NET Framework derlemeleri özel öznitelikler özel öznitelikleri depolamak ve derlemeler, türleri, üyeleri ve yöntem parametreleri gibi nesneler programlama hakkındaki meta verilerini alma için genişletilebilir bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="d51c0-628">In.NET Framework assemblies, custom attributes provide an extensible mechanism for storing custom attributes and retrieving metadata about programming objects, such as assemblies, types, members, and method parameters.</span></span> <span data-ttu-id="d51c0-629">Özel öznitelikler öğesinden türetilmelidir [System.Attribute'un](xref:System.Attribute) veya türetilmiş bir türden `System.Attribute`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-629">Custom attributes must derive from [System.Attribute](xref:System.Attribute) or from a type derived from `System.Attribute`.</span></span>

<span data-ttu-id="d51c0-630">Aşağıdaki örnek, bu kural ihlal ediyor.</span><span class="sxs-lookup"><span data-stu-id="d51c0-630">The following example violates this rule.</span></span> <span data-ttu-id="d51c0-631">Bunu tanımlayan bir `NumericAttribute` türünden türemez sınıfı `System.Attribute`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-631">It defines a `NumericAttribute` class that does not derive from `System.Attribute`.</span></span> <span data-ttu-id="d51c0-632">Derleyici Hatası sınıfı tanımlanmadığında yalnızca zaman CLS uyumlu olmayan özniteliği, uygulanan sonuçları unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d51c0-632">Note that a compiler error results only when the non-CLS-compliant attribute is applied, not when the class is defined.</span></span> 

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

<span data-ttu-id="d51c0-633">Oluşturucunun ya da CLS uyumlu bir özniteliğin özelliklerini yalnızca şu türleri getirebilir:</span><span class="sxs-lookup"><span data-stu-id="d51c0-633">The constructor or the properties of a CLS-compliant attribute can expose only the following types:</span></span>

* [<span data-ttu-id="d51c0-634">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="d51c0-634">Boolean</span></span>](xref:System.Boolean)

* [<span data-ttu-id="d51c0-635">Bayt</span><span class="sxs-lookup"><span data-stu-id="d51c0-635">Byte</span></span>](xref:System.Byte)

* [<span data-ttu-id="d51c0-636">char</span><span class="sxs-lookup"><span data-stu-id="d51c0-636">Char</span></span>](xref:System.Char)

* [<span data-ttu-id="d51c0-637">Çift</span><span class="sxs-lookup"><span data-stu-id="d51c0-637">Double</span></span>](xref:System.Double)

* [<span data-ttu-id="d51c0-638">Int16</span><span class="sxs-lookup"><span data-stu-id="d51c0-638">Int16</span></span>](xref:System.Int16)

* [<span data-ttu-id="d51c0-639">Int32</span><span class="sxs-lookup"><span data-stu-id="d51c0-639">Int32</span></span>](xref:System.Int32)

* [<span data-ttu-id="d51c0-640">Int64</span><span class="sxs-lookup"><span data-stu-id="d51c0-640">Int64</span></span>](xref:System.Int64)

* [<span data-ttu-id="d51c0-641">Tek</span><span class="sxs-lookup"><span data-stu-id="d51c0-641">Single</span></span>](xref:System.Single)

* [<span data-ttu-id="d51c0-642">Dize</span><span class="sxs-lookup"><span data-stu-id="d51c0-642">String</span></span>](xref:System.String)

* [<span data-ttu-id="d51c0-643">Türü</span><span class="sxs-lookup"><span data-stu-id="d51c0-643">Type</span></span>](xref:System.Type)

* <span data-ttu-id="d51c0-644">Temel alınan türü olan herhangi bir numaralandırma türü `Byte`, `Int16`, `Int32`, veya `Int64`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-644">Any enumeration type whose underlying type is `Byte`, `Int16`, `Int32`, or `Int64`.</span></span> 

<span data-ttu-id="d51c0-645">Aşağıdaki örnek tanımlayan bir `DescriptionAttribute` öğesinden türetilen sınıf [özniteliği](xref:System.Attribute).</span><span class="sxs-lookup"><span data-stu-id="d51c0-645">The following example defines a `DescriptionAttribute` class that derives from [Attribute](xref:System.Attribute).</span></span> <span data-ttu-id="d51c0-646">Türünde bir parametre sınıfı kurucusunun `Descriptor`, bu sınıf CLS uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="d51c0-646">The class constructor has a parameter of type `Descriptor`, so the class is not CLS-compliant.</span></span> <span data-ttu-id="d51c0-647">C# Derleyici bir uyarı gösterir ancak başarıyla derlenen unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d51c0-647">Note that the C# compiler emits a warning but compiles successfully.</span></span> 

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

## <a name="the-clscompliantattribute-attribute"></a><span data-ttu-id="d51c0-648">CLSCompliantAttribute özniteliği</span><span class="sxs-lookup"><span data-stu-id="d51c0-648">The CLSCompliantAttribute attribute</span></span>

<span data-ttu-id="d51c0-649">[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) öznitelik, bir program öğesi ortak dil belirtimi ile uyumlu olup olmadığını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-649">The [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is used to indicate whether a program element complies with the Common Language Specification.</span></span> <span data-ttu-id="d51c0-650">`CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` Oluşturucusu içeren tek bir gerekli parametre *isCompliant*, bir program öğesi CLS ile uyumlu olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-650">The `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` constructor includes a single required parameter, *isCompliant*, that indicates whether the program element is CLS-compliant.</span></span> 

<span data-ttu-id="d51c0-651">Derleme zamanında derleyici CLS ile uyumlu olması için varsayılan ve bir uyarı yayar uyumlu olmayan öğeler algılar.</span><span class="sxs-lookup"><span data-stu-id="d51c0-651">At compile time, the compiler detects non-compliant elements that are presumed to be CLS-compliant and emits a warning.</span></span> <span data-ttu-id="d51c0-652">Derleyici uyarıları türler veya uyumlu olması için açıkça bildirilen üyeler için yayma değil.</span><span class="sxs-lookup"><span data-stu-id="d51c0-652">The compiler does not emit warnings for types or members that are explicitly declared to be non-compliant.</span></span> 

<span data-ttu-id="d51c0-653">Bileşen geliştiricileri kullanabilir `CLSCompliantAttribute` öznitelik iki yolla:</span><span class="sxs-lookup"><span data-stu-id="d51c0-653">Component developers can use the `CLSCompliantAttribute` attribute in two ways:</span></span> 

* <span data-ttu-id="d51c0-654">CLS uyumlu bir bileşen tarafından kullanıma sunulan ortak arabirimi bölümlerini ve CLS uyumlu olmayan bölümleri tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="d51c0-654">To define the parts of the public interface exposed by a component that are CLS-compliant and the parts that are not CLS-compliant.</span></span> <span data-ttu-id="d51c0-655">Kullanımı öznitelik belirli programın öğeleri CLS ile uyumlu işaretlemek için kullanıldığında, bu öğeleri tüm diller ve .NET Framework hedefleyen Araçlar menüsünden erişilebilir olduğunu güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-655">When the attribute is used to mark particular program elements as CLS-compliant, its use guarantees that those elements are accessible from all languages and tools that target the .NET Framework.</span></span> 

* <span data-ttu-id="d51c0-656">Bileşen kitaplığın ortak arabirim, CLS uyumlu program öğelerini oluşturduğuna emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="d51c0-656">To ensure that the component library's public interface exposes only program elements that are CLS-compliant.</span></span> <span data-ttu-id="d51c0-657">Öğeleri CLS ile uyumlu değilse, derleyicileri genellikle bir uyarı verecek.</span><span class="sxs-lookup"><span data-stu-id="d51c0-657">If elements are not CLS-compliant, compilers will generally issue a warning.</span></span>

> [!WARNING]
> <span data-ttu-id="d51c0-658">Bazı durumlarda, dil derleyicileri mi bakılmaksızın CLS uyumlu kuralları zorla `CLSCompliantAttribute` özniteliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-658">In some cases, language compilers enforce CLS-compliant rules regardless of whether the `CLSCompliantAttribute` attribute is used.</span></span> <span data-ttu-id="d51c0-659">Örneğin, tanımlayan bir `*static` bir arabirim üye CLS kuralını ihlal ediyor.</span><span class="sxs-lookup"><span data-stu-id="d51c0-659">For example, defining a `*static` member in an interface violates a CLS rule.</span></span> <span data-ttu-id="d51c0-660">Ancak, tanımlarsanız bir `*static` bir arabirim üye, C# Derleyici bir hata iletisi ile başarısız uygulama derlemek için görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d51c0-660">However, if you define a `*static` member in an interface, the C# compiler displays an error message and fails to compile the app.</span></span>

<span data-ttu-id="d51c0-661">`CLSCompliantAttribute` Özniteliği ile işaretlenmiş bir [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) değerine sahip öznitelik `AttributeTargets.All`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-661">The `CLSCompliantAttribute` attribute is marked with an [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) attribute that has a value of `AttributeTargets.All`.</span></span> <span data-ttu-id="d51c0-662">Bu değer uygulamanıza imkan sağlayan `CLSCompliantAttribute` özniteliği derlemeler, modüller de dahil olmak üzere herhangi bir program öğesi için türleri (sınıflar, yapılar, numaralandırmalar, arabirimler ve temsilciler), üyeleri (Oluşturucular, yöntemler, özellikler, alanları ve olaylar), yazın Parametreler, genel parametreler ve dönüş değerleri.</span><span class="sxs-lookup"><span data-stu-id="d51c0-662">This value allows you to apply the `CLSCompliantAttribute` attribute to any program element, including assemblies, modules, types (classes, structures, enumerations, interfaces, and delegates), type members (constructors, methods, properties, fields, and events), parameters, generic parameters, and return values.</span></span> <span data-ttu-id="d51c0-663">Bununla birlikte, pratikte, öznitelik yalnızca derlemeler, türleri ve tür üyeleri uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-663">However, in practice, you should apply the attribute only to assemblies, types, and type members.</span></span> <span data-ttu-id="d51c0-664">Aksi takdirde derleyicileri öznitelik yoksay ve her genel parametresi, uyumlu olmayan bir parametre karşılaştığınız veya dönüş değeri kitaplığınızın ortak arabiriminde derleyici uyarıları oluşturmaya devam.</span><span class="sxs-lookup"><span data-stu-id="d51c0-664">Otherwise, compilers ignore the attribute and continue to generate compiler warnings whenever they encounter a non-compliant parameter, generic parameter, or return value in your library's public interface.</span></span>  

<span data-ttu-id="d51c0-665">Değeri `CLSCompliantAttribute` özniteliği kapsanan program öğeleri tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-665">The value of the `CLSCompliantAttribute` attribute is inherited by contained program elements.</span></span> <span data-ttu-id="d51c0-666">Bir derlemeyi CLS ile uyumlu işaretlenmişse, örneğin, türlerinden ayrıca CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-666">For example, if an assembly is marked as CLS-compliant, its types are also CLS-compliant.</span></span> <span data-ttu-id="d51c0-667">Bir tür CLS ile uyumlu işaretlenmişse, kendi iç içe geçmiş türler ve üyeleri ayrıca CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-667">If a type is marked as CLS-compliant, its nested types and members are also CLS-compliant.</span></span> 

<span data-ttu-id="d51c0-668">Devralınan uyumluluk uygulayarak açıkça geçersiz kılabilirsiniz `CLSCompliantAttribute` özniteliği kapsanan bir program öğesi için.</span><span class="sxs-lookup"><span data-stu-id="d51c0-668">You can explicitly override the inherited compliance by applying the `CLSCompliantAttribute` attribute to a contained program element.</span></span> <span data-ttu-id="d51c0-669">Örneğin, kullanabileceğiniz `CLSCompliantAttribute` ile öznitelik bir *isCompliant* değerini `false` uyumlu bir derleme ve, uyumlu olmayan bir tür tanımlamak için öznitelik kullanabilirsiniz bir *isComplian*değerini `true` uyumlu bir türü uyumlu olmayan bir derlemede tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="d51c0-669">For example, you can use the `CLSCompliantAttribute` attribute with an *isCompliant* value of `false` to define a non-compliant type in a compliant assembly, and you can use the attribute with an *isComplian* value of `true` to define a compliant type in a non-compliant assembly.</span></span> <span data-ttu-id="d51c0-670">Ayrıca, uyumlu bir türü uyumlu olmayan üyeler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d51c0-670">You can also define non-compliant members in a compliant type.</span></span> <span data-ttu-id="d51c0-671">Ancak, dolayısıyla özniteliğiyle kullanamaz uyumlu üyeler uyumlu olmayan bir türü olamaz bir *isCompliant* değerini `true` uyumlu olmayan türünden devralma geçersiz kılmak için.</span><span class="sxs-lookup"><span data-stu-id="d51c0-671">However, a non-compliant type cannot have compliant members, so you cannot use the attribute with an *isCompliant* value of `true` to override inheritance from a non-compliant type.</span></span> 

<span data-ttu-id="d51c0-672">Bileşenleri geliştirirken, her zaman kullanmalısınız `CLSCompliantAttribute` derlemenizi, kendi türleri ve üyeleri CLS ile uyumlu olup olmadığını belirtmek için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d51c0-672">When you are developing components, you should always use the `CLSCompliantAttribute` attribute to indicate whether your assembly, its types, and its members are CLS-compliant.</span></span> 

<span data-ttu-id="d51c0-673">CLS uyumlu bileşenleri oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="d51c0-673">To create CLS-compliant components:</span></span> 

1. <span data-ttu-id="d51c0-674">Kullanım `CLSCompliantAttribute` Derleme CLS uyumlu olarak işaretlemek için.</span><span class="sxs-lookup"><span data-stu-id="d51c0-674">Use the `CLSCompliantAttribute` to mark you assembly as CLS-compliant.</span></span>

2. <span data-ttu-id="d51c0-675">CLS uyumlu olarak uyumlu olmayan derlemesindeki genel olarak sunulan türler işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="d51c0-675">Mark any publicly exposed types in the assembly that are not CLS-compliant as non-compliant.</span></span> 

3. <span data-ttu-id="d51c0-676">CLS uyumlu türleri uyumsuz olarak genel kullanıma sunulan tüm üyelerinde işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="d51c0-676">Mark any publicly exposed members in CLS-compliant types as non-compliant.</span></span> 

4. <span data-ttu-id="d51c0-677">CLS uyumlu alternatifi CLS uyumlu olmayan üyeler için sağlar.</span><span class="sxs-lookup"><span data-stu-id="d51c0-677">Provide a CLS-compliant alternative for non-CLS-compliant members.</span></span> 

<span data-ttu-id="d51c0-678">Tüm uyumlu olmayan türleri ve üyeleri başarıyla işaretlediyseniz, derleyici hiçbir uyumsuzluk uyarıları yayma değil.</span><span class="sxs-lookup"><span data-stu-id="d51c0-678">If you've successfully marked all your non-compliant types and members, your compiler should not emit any non-compliance warnings.</span></span> <span data-ttu-id="d51c0-679">Ancak, hangi üyeleri CLS uyumlu değildir ve bunların CLS uyumlu alternatifleri, ürün belgelerinde listesinde belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-679">However, you should indicate which members are not CLS-compliant and list their CLS-compliant alternatives in your product documentation.</span></span> 

<span data-ttu-id="d51c0-680">Aşağıdaki örnek kullanır `CLSCompliantAttribute` CLS uyumlu bir derleme ve bir tür tanımlamak için öznitelik `CharacterUtilities`, iki CLS uyumlu olmayan üyeler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="d51c0-680">The following example uses the `CLSCompliantAttribute` attribute to define a CLS-compliant assembly and a type, `CharacterUtilities`, that has two non-CLS-compliant members.</span></span> <span data-ttu-id="d51c0-681">Her iki üyeleri ile etiketlenir çünkü `CLSCompliant(false)` özniteliği, derleyici hiçbir uyarılar üretir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-681">Because both members are tagged with the `CLSCompliant(false)` attribute, the compiler produces no warnings.</span></span> <span data-ttu-id="d51c0-682">Sınıf, CLS uyumlu alternatifi için iki yöntem de sağlar.</span><span class="sxs-lookup"><span data-stu-id="d51c0-682">The class also provides a CLS-compliant alternative for both methods.</span></span> <span data-ttu-id="d51c0-683">Normalde, biz yalnızca iki aşırı eklediğiniz `ToUTF16` yöntem CLS uyumlu alternatifleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="d51c0-683">Ordinarily, we would just add two overloads to the `ToUTF16` method to provide CLS-compliant alternatives.</span></span> <span data-ttu-id="d51c0-684">Ancak, dönüş değerini temel yöntemlerini aşırı yüklenemez olduğundan, uyumlu olmayan yöntemleri adlarından adları CLS uyumlu yöntemlerin farklıdır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-684">However, because methods cannot be overloaded based on return value, the names of the CLS-compliant methods are different from the names of the non-compliant methods.</span></span>  

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

<span data-ttu-id="d51c0-685">Varsa (diğer bir deyişle, türler veya diğer uygulama geliştiriciler tarafından kullanılan üyeler gösterme değil ise) bir kitaplık yerine bir uygulama geliştirdiğiniz, uygulamanızı tüketen program öğelerin CLS uyumluluğu ilgi yalnızca dilinizi bunları desteklemiyorsa .</span><span class="sxs-lookup"><span data-stu-id="d51c0-685">If you are developing an app rather than a library (that is, if you aren't exposing types or members that can be consumed by other app developers), the CLS compliance of the program elements that your app consumes are of interest only if your language does not support them.</span></span> <span data-ttu-id="d51c0-686">Bu durumda, CLS uyumlu olmayan bir öğe kullanmaya çalıştığınızda, dil derleyici bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d51c0-686">In that case, your language compiler will generate an error when you try to use a non-CLS-compliant element.</span></span> 

## <a name="cross-language-interoperability"></a><span data-ttu-id="d51c0-687">Diller Arası Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="d51c0-687">Cross-Language Interoperability</span></span>

<span data-ttu-id="d51c0-688">Dil bağımsızlığının birkaç olası anlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-688">Language independence has a number of possible meanings.</span></span> <span data-ttu-id="d51c0-689">Sorunsuz bir şekilde başka bir dilde bir uygulamadan bir dilinde yazılmış türlerini kullanan bir anlam içerir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-689">One meaning involves seamlessly consuming types written in one language from an app written in another language.</span></span> <span data-ttu-id="d51c0-690">Bu makalenin konusu olan ikinci anlamı ise, birden çok dilde yazılmış kodu tek bir .NET Framework derlemesi olarak birleştirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-690">A second meaning, which is the focus of this article, involves combining code written in multiple languages into a single .NET Framework assembly.</span></span> 

<span data-ttu-id="d51c0-691">Aşağıdaki örnekte, iki sınıf içerir Utilities.dll adlı bir sınıf kitaplığı oluşturarak diller arası birlikte çalışabilirlik gösterilmektedir `NumericLib` ve `StringLib`.</span><span class="sxs-lookup"><span data-stu-id="d51c0-691">The following example illustrates cross-language interoperability by creating a class library named Utilities.dll that includes two classes, `NumericLib` and `StringLib`.</span></span> <span data-ttu-id="d51c0-692">`NumericLib` Sınıfı yazılır C# ' ta ve `StringLib` sınıfı, Visual Basic'te yazılır.</span><span class="sxs-lookup"><span data-stu-id="d51c0-692">The `NumericLib` class is written in C#, and the `StringLib` class is written in Visual Basic.</span></span> <span data-ttu-id="d51c0-693">Kaynak kodu işte `StringUtil.vb`, tek bir üyeyi içeren `ToTitleCase`, kendi `StringLib` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d51c0-693">Here's the source code for `StringUtil.vb`, which includes a single member, `ToTitleCase`, in its `StringLib` class.</span></span>

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

<span data-ttu-id="d51c0-694">Aşağıda `NumericLib` ve `IsEven` olmak üzere iki üyesi olan bir `NearZero` sınıfını tanımlayan NumberUtil.cs için kaynak kodu verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-694">Here's the source code for NumberUtil.cs, which defines a `NumericLib` class that has two members, `IsEven` and `NearZero`.</span></span>

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

<span data-ttu-id="d51c0-695">Tek bir derleme iki sınıflarda paketlemek için modüllerine derlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d51c0-695">To package the two classes in a single assembly, you must compile them into modules.</span></span> <span data-ttu-id="d51c0-696">Visual Basic kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d51c0-696">To compile the Visual Basic source code file into a module, use this command:</span></span> 

```
vbc /t:module StringUtil.vb 
```

<span data-ttu-id="d51c0-697">C# kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d51c0-697">To compile the C# source code file into a module, use this command:</span></span>

```
csc /t:module NumberUtil.cs
```

<span data-ttu-id="d51c0-698">Bir derlemeye iki modülleri derlemek için bağlantı aracını (Link.exe) kullanın:</span><span class="sxs-lookup"><span data-stu-id="d51c0-698">You then use the Link tool (Link.exe) to compile the two modules into an assembly:</span></span> 

```
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

<span data-ttu-id="d51c0-699">Aşağıdaki örnek daha sonra çağırır `NumericLib.NearZero` ve `StringLib.ToTitleCase` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="d51c0-699">The following example then calls the `NumericLib.NearZero` and `StringLib.ToTitleCase` methods.</span></span> <span data-ttu-id="d51c0-700">Visual Basic kodu ve C# kodu her iki sınıfları yöntemleri erişebilir olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="d51c0-700">Note that both the Visual Basic code and the C# code are able to access the methods in both classes.</span></span>

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

<span data-ttu-id="d51c0-701">Visual Basic kodunu derlemek için bu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d51c0-701">To compile the Visual Basic code, use this command:</span></span>

```
vbc example.vb /r:UtilityLib.dll
```

<span data-ttu-id="d51c0-702">C# ile derlemek için csc için vbc derleyici adını değiştirmek ve dosya uzantısını .cs için .vb değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d51c0-702">To compile with C#, change the name of the compiler from vbc to csc, and change the file extension from .vb to .cs:</span></span>

```
csc example.cs /r:UtilityLib.dll
```

