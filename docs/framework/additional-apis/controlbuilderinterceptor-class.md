---
title: ControlBuilderInterceptor sınıfı
ms.date: 08/11/2020
api_name:
- System.Web.Compilation.ControlBuilderInterceptor
api_location:
- System.Web.dll
api_type:
- Assembly
topic_type:
- apiref
ms.openlocfilehash: 0cd7409deb9cb84783cfa70600999fa4b2a2d2e2
ms.sourcegitcommit: d337df55f83325918cbbd095eb573400bea49064
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88187992"
---
# <a name="controlbuilderinterceptor-class"></a><span data-ttu-id="b26dc-102">ControlBuilderInterceptor sınıfı</span><span class="sxs-lookup"><span data-stu-id="b26dc-102">ControlBuilderInterceptor class</span></span>

<span data-ttu-id="b26dc-103">`ControlBuilderInterceptor`Sınıfı, derleme işleminin özelleştirilme veya kontrollü olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b26dc-103">The `ControlBuilderInterceptor` class allows the compilation process to be customized or controlled.</span></span>

## <a name="syntax"></a><span data-ttu-id="b26dc-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b26dc-104">Syntax</span></span>

```csharp
internal class ControlBuilderInterceptor
```

> [!WARNING]
> <span data-ttu-id="b26dc-105">`ControlBuilderInterceptor`Sınıfı dahili ve doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="b26dc-105">The `ControlBuilderInterceptor` class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="b26dc-106">Açıklamalar bölümünde açıklandığı gibi, bu türün varlığı, yakacının tür desteğinin mevcut olup olmadığını tespit etmek için denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b26dc-106">As described in the Remarks section, the existence of this type can be checked to determine whether interceptor type support is present.</span></span> <span data-ttu-id="b26dc-107">Microsoft, herhangi bir koşulda bu sınıfın başka bir kullanımını bir üretim uygulamasında desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b26dc-107">Microsoft does not support any other use of this class in a production application under any circumstance.</span></span>

## <a name="remarks"></a><span data-ttu-id="b26dc-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b26dc-108">Remarks</span></span>

<span data-ttu-id="b26dc-109">.NET Framework 2,0 ve .NET Framework 3,5 ' de, [ağustos 2020](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug) güncelleştirme, derleme işlemini özelleştirmek veya denetlemek için bir dinleyici türü kullanma desteği eklemiştir.</span><span class="sxs-lookup"><span data-stu-id="b26dc-109">In .NET Framework 2.0 and .NET Framework 3.5, the [August 2020](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug) updates added support for using an interceptor type to customize or control the compilation process.</span></span> <span data-ttu-id="b26dc-110"><xref:System.Type.GetType?displayProperty=nameWithType> `ControlBuilderInterceptor` Aşağıdaki kodda gösterildiği gibi, türün varlığını denetlemek için kullanarak bu desteğin mevcut olup olmadığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b26dc-110">You can determine whether this support is present by using <xref:System.Type.GetType?displayProperty=nameWithType> to check the existence of the `ControlBuilderInterceptor` type, as demonstrated in the following code.</span></span>

```csharp
Type type = Type.GetType("System.Web.Compilation.ControlBuilderInterceptor, System.Web, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a");
```

<span data-ttu-id="b26dc-111">Dönüş değeri null değilse, şifre veren desteği vardır.</span><span class="sxs-lookup"><span data-stu-id="b26dc-111">If the return value is non-null, then interceptor support is present.</span></span> <span data-ttu-id="b26dc-112">Dönüş değeri ise `null` veya bir özel durum oluşturulursa, ağustos 2020 güncelleştirmeleri yüklenmemiştir ve şifre oluşturma desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="b26dc-112">If the return value is `null`, or if an exception is thrown, then the August 2020 updates have not been installed, and interceptor support is absent.</span></span>

<span data-ttu-id="b26dc-113">Eğer şifre işleme desteği varsa, .NET Framework sonraki sürümlerinde tam olarak aynı şekilde, derleme işlemiyle etkileşim kuracak bir dinleyici türü yazabilir ve kaydedebilirsiniz <xref:System.Web.Compilation.ControlBuilderInterceptor> .</span><span class="sxs-lookup"><span data-stu-id="b26dc-113">If interceptor support is present, you can write and register an interceptor type that will interact with the compilation process in exactly the same way that <xref:System.Web.Compilation.ControlBuilderInterceptor> does on later versions of .NET Framework.</span></span> <span data-ttu-id="b26dc-114">.NET Framework 2,0 ve .NET Framework 3,5 ' de, yakalayıcısı türü aşağıdaki gereksinimleri karşılayan herhangi bir sınıf olabilir:</span><span class="sxs-lookup"><span data-stu-id="b26dc-114">In .NET Framework 2.0 and .NET Framework 3.5, the interceptor type can be any class that meets the following requirements:</span></span>

* <span data-ttu-id="b26dc-115">Ortak, parametresiz bir oluşturucuya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b26dc-115">Has a public, parameterless constructor.</span></span>
* <span data-ttu-id="b26dc-116">, `PreControlBuilderInit` `OnProcessGeneratedCode` <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> Daha sonraki .NET Framework sürümlerde bulunan ve yöntemleriyle aynı imzaya ve semantiğe sahip olan ve adlı ortak, statik olmayan yöntemlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b26dc-116">Has public, non-static methods named `PreControlBuilderInit` and `OnProcessGeneratedCode` that have the same signature and semantics as the <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> and <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> methods, which exist in later versions of .NET Framework.</span></span>

<span data-ttu-id="b26dc-117">`aspnet:20ControlBuilderInterceptor`ASP.NET uygulama ayarları () içindeki anahtarı kullanarak yakalayıcıyı türünü kaydedin `<appSettings>` .</span><span class="sxs-lookup"><span data-stu-id="b26dc-117">Register the interceptor type by using the `aspnet:20ControlBuilderInterceptor` key in ASP.NET application settings (`<appSettings>`).</span></span> <span data-ttu-id="b26dc-118">Bu uygulama ayarı bilgisayarınızda veya uygulama *web.config* dosyanızda listelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="b26dc-118">This application setting must be listed in your computer or application *web.config* file.</span></span> <span data-ttu-id="b26dc-119">Onun derleme nitelikli tür adını kullanarak yakalayıcıyı türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="b26dc-119">Specify the interceptor type by using its assembly-qualified type name.</span></span> <span data-ttu-id="b26dc-120">Aşağıdaki örnek, adlı bir yakalayıcısı türünün nasıl kaydedileceği gösterilmektedir `Fabrikam.Interceptor` .</span><span class="sxs-lookup"><span data-stu-id="b26dc-120">The following example shows how to register an interceptor type named `Fabrikam.Interceptor`.</span></span>

```xml
<configuration>
  ...
  <appSettings>
    ...
    <add key="aspnet:20ControlBuilderInterceptor"
         value="Fabrikam.Interceptor, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
  </appSettings>
</configuration>
```

<span data-ttu-id="b26dc-121">Bir türün derleme nitelikli adını almak için <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> aşağıdaki kodda gösterildiği gibi özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b26dc-121">To retrieve the assembly-qualified name of a type, use the <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> property, as demonstrated in the following code.</span></span>

```csharp
string assemblyQualifiedName = typeof(Fabrikam.Interceptor).AssemblyQualifiedName;
```

<span data-ttu-id="b26dc-122">Şifre işleme desteği mevcut olduğunda, derleme işlemi yukarıda açıklanan şekilde listelenen türle etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="b26dc-122">When interceptor support is present, the compilation process interacts with the listed type in the manner described above.</span></span> <span data-ttu-id="b26dc-123">Yakalayıcıyı destekliyorsa, uygulama ayarı yok sayılır ve etkisizdir.</span><span class="sxs-lookup"><span data-stu-id="b26dc-123">When interceptor support is absent, the application setting is ignored and has no effect.</span></span>

## <a name="requirements"></a><span data-ttu-id="b26dc-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b26dc-124">Requirements</span></span>

<span data-ttu-id="b26dc-125">**Ad alanı:** System. Web. Compilation</span><span class="sxs-lookup"><span data-stu-id="b26dc-125">**Namespace:** System.Web.Compilation</span></span>

<span data-ttu-id="b26dc-126">**Bütünleştirilmiş kod:** System. Web (System.Web.dll)</span><span class="sxs-lookup"><span data-stu-id="b26dc-126">**Assembly:** System.Web (in System.Web.dll)</span></span>

<span data-ttu-id="b26dc-127">**.NET Framework sürümleri:** 3,5, 2,0</span><span class="sxs-lookup"><span data-stu-id="b26dc-127">**.NET Framework versions:** 3.5, 2.0</span></span>
