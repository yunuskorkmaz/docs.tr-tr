---
title: Platform Çağırma ile Veri Sıralama
ms.date: 03/20/2019
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3167abd0c263a0a27573778d6f243bc824306a9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051683"
---
# <a name="marshaling-data-with-platform-invoke"></a><span data-ttu-id="83185-102">Platform Çağırma ile Veri Sıralama</span><span class="sxs-lookup"><span data-stu-id="83185-102">Marshaling Data with Platform Invoke</span></span>

<span data-ttu-id="83185-103">Yönetilmeyen bir kitaplıktan aktarılmış işlevleri çağırmak için, bir .NET Framework uygulaması yönetilmeyen işlevi temsil eden yönetilen kodda bir işlev prototipi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="83185-103">To call functions exported from an unmanaged library, a .NET Framework application requires a function prototype in managed code that represents the unmanaged function.</span></span> <span data-ttu-id="83185-104">Platform Invoke 'ın verileri doğru bir şekilde sıralaması için bir prototip oluşturmak üzere şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="83185-104">To create a prototype that enables platform invoke to marshal data correctly, you must do the following:</span></span>

- <span data-ttu-id="83185-105"><xref:System.Runtime.InteropServices.DllImportAttribute> Özniteliği, Yönetilen koddaki statik işleve veya yöntemine uygulayın.</span><span class="sxs-lookup"><span data-stu-id="83185-105">Apply the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to the static function or method in managed code.</span></span>

- <span data-ttu-id="83185-106">Yönetilmeyen veri türleri için yönetilen veri türlerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="83185-106">Substitute managed data types for unmanaged data types.</span></span>

<span data-ttu-id="83185-107">Özniteliği isteğe bağlı alanlarıyla uygulayıp yönetilmeyen türler için yönetilen veri türlerini değiştirerek eşdeğer bir yönetilen prototip oluşturmak için, yönetilmeyen bir işlevle sağlanan belgeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83185-107">You can use the documentation supplied with an unmanaged function to construct an equivalent managed prototype by applying the attribute with its optional fields and substituting managed data types for unmanaged types.</span></span> <span data-ttu-id="83185-108">Uygulamasına nasıl uygulandığına <xref:System.Runtime.InteropServices.DllImportAttribute>ilişkin yönergeler için bkz. [yönetilmeyen DLL işlevlerini](consuming-unmanaged-dll-functions.md)kullanma.</span><span class="sxs-lookup"><span data-stu-id="83185-108">For instructions about how to apply the <xref:System.Runtime.InteropServices.DllImportAttribute>, see [Consuming Unmanaged DLL Functions](consuming-unmanaged-dll-functions.md).</span></span>

<span data-ttu-id="83185-109">Bu bölümde, yönetilmeyen kitaplıklar tarafından dışarıya aktarılmış işlevlerden gelen bağımsız değişkenleri iletmek ve dönüş değerlerini almak için yönetilen işlev prototürlerinin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="83185-109">This section provides samples that demonstrate how to create managed function prototypes for passing arguments to and receiving return values from functions exported by unmanaged libraries.</span></span> <span data-ttu-id="83185-110">Örnekler Ayrıca, <xref:System.Runtime.InteropServices.MarshalAsAttribute> verileri açıkça sıralamak için özniteliği <xref:System.Runtime.InteropServices.Marshal> ve sınıfını ne zaman kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="83185-110">The samples also demonstrate when to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute and the <xref:System.Runtime.InteropServices.Marshal> class to explicitly marshal data.</span></span>

## <a name="platform-invoke-data-types"></a><span data-ttu-id="83185-111">Platform çağırma veri türleri</span><span class="sxs-lookup"><span data-stu-id="83185-111">Platform invoke data types</span></span>

<span data-ttu-id="83185-112">Aşağıdaki tabloda, Windows API 'Leri ve C stili işlevlerinde kullanılan veri türleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="83185-112">The following table lists data types used in the Windows APIs and C-style functions.</span></span> <span data-ttu-id="83185-113">Birçok yönetilmeyen kitaplık, bu veri türlerini parametre olarak geçen ve değer döndüren işlevleri içerir.</span><span class="sxs-lookup"><span data-stu-id="83185-113">Many unmanaged libraries contain functions that pass these data types as parameters and return values.</span></span> <span data-ttu-id="83185-114">Üçüncü sütunda karşılık gelen .NET Framework yerleşik değer türü veya yönetilen kodda kullandığınız sınıf listelenir.</span><span class="sxs-lookup"><span data-stu-id="83185-114">The third column lists the corresponding .NET Framework built-in value type or class that you use in managed code.</span></span> <span data-ttu-id="83185-115">Bazı durumlarda, tabloda listelenen tür için aynı boyuttaki bir türü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83185-115">In some cases, you can substitute a type of the same size for the type listed in the table.</span></span>

|<span data-ttu-id="83185-116">Windows API 'Lerinde yönetilmeyen tür</span><span class="sxs-lookup"><span data-stu-id="83185-116">Unmanaged type in Windows APIs</span></span>|<span data-ttu-id="83185-117">Yönetilmeyen C dil türü</span><span class="sxs-lookup"><span data-stu-id="83185-117">Unmanaged C language type</span></span>|<span data-ttu-id="83185-118">Yönetilen tür</span><span class="sxs-lookup"><span data-stu-id="83185-118">Managed type</span></span>|<span data-ttu-id="83185-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83185-119">Description</span></span>|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|<span data-ttu-id="83185-120">Değer döndürmeyen bir işleve uygulandı.</span><span class="sxs-lookup"><span data-stu-id="83185-120">Applied to a function that does not return a value.</span></span>|
|`HANDLE`|`void *`|<span data-ttu-id="83185-121"><xref:System.IntPtr?displayProperty=nameWithType> veya <xref:System.UIntPtr?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="83185-121"><xref:System.IntPtr?displayProperty=nameWithType> or <xref:System.UIntPtr?displayProperty=nameWithType></span></span>|<span data-ttu-id="83185-122">32 bit Windows işletim sistemlerinde 32 bit, 64 bit Windows işletim sistemlerinde 64 bit.</span><span class="sxs-lookup"><span data-stu-id="83185-122">32 bits on 32-bit Windows operating systems, 64 bits on 64-bit Windows operating systems.</span></span>|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="83185-123">8 bit</span><span class="sxs-lookup"><span data-stu-id="83185-123">8 bits</span></span>|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="83185-124">16 bit</span><span class="sxs-lookup"><span data-stu-id="83185-124">16 bits</span></span>|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="83185-125">16 bit</span><span class="sxs-lookup"><span data-stu-id="83185-125">16 bits</span></span>|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="83185-126">32 bit</span><span class="sxs-lookup"><span data-stu-id="83185-126">32 bits</span></span>|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="83185-127">32 bit</span><span class="sxs-lookup"><span data-stu-id="83185-127">32 bits</span></span>|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="83185-128">32 bit</span><span class="sxs-lookup"><span data-stu-id="83185-128">32 bits</span></span>|
|`BOOL`|`long`|<span data-ttu-id="83185-129"><xref:System.Boolean?displayProperty=nameWithType> veya <xref:System.Int32?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="83185-129"><xref:System.Boolean?displayProperty=nameWithType> or <xref:System.Int32?displayProperty=nameWithType></span></span>|<span data-ttu-id="83185-130">32 bit</span><span class="sxs-lookup"><span data-stu-id="83185-130">32 bits</span></span>|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="83185-131">32 bit</span><span class="sxs-lookup"><span data-stu-id="83185-131">32 bits</span></span>|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="83185-132">32 bit</span><span class="sxs-lookup"><span data-stu-id="83185-132">32 bits</span></span>|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="83185-133">ANSI ile süslemek.</span><span class="sxs-lookup"><span data-stu-id="83185-133">Decorate with ANSI.</span></span>|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="83185-134">Unicode ile süsle.</span><span class="sxs-lookup"><span data-stu-id="83185-134">Decorate with Unicode.</span></span>|
|`LPSTR`|`char *`|<span data-ttu-id="83185-135"><xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="83185-135"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="83185-136">ANSI ile süslemek.</span><span class="sxs-lookup"><span data-stu-id="83185-136">Decorate with ANSI.</span></span>|
|`LPCSTR`|`const char *`|<span data-ttu-id="83185-137"><xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="83185-137"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="83185-138">ANSI ile süslemek.</span><span class="sxs-lookup"><span data-stu-id="83185-138">Decorate with ANSI.</span></span>|
|`LPWSTR`|`wchar_t *`|<span data-ttu-id="83185-139"><xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="83185-139"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="83185-140">Unicode ile süsle.</span><span class="sxs-lookup"><span data-stu-id="83185-140">Decorate with Unicode.</span></span>|
|`LPCWSTR`|`const wchar_t *`|<span data-ttu-id="83185-141"><xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="83185-141"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="83185-142">Unicode ile süsle.</span><span class="sxs-lookup"><span data-stu-id="83185-142">Decorate with Unicode.</span></span>|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="83185-143">32 bit</span><span class="sxs-lookup"><span data-stu-id="83185-143">32 bits</span></span>|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="83185-144">64 bit</span><span class="sxs-lookup"><span data-stu-id="83185-144">64 bits</span></span>|

<span data-ttu-id="83185-145">Visual Basic, C#ve C++' deki Ilgili türler Için [.NET Framework sınıfı kitaplığına giriş](../../standard/class-library-overview.md#system-namespace)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="83185-145">For corresponding types in Visual Basic, C#, and C++, see the [Introduction to the .NET Framework Class Library](../../standard/class-library-overview.md#system-namespace).</span></span>

## <a name="pinvokelibdll"></a><span data-ttu-id="83185-146">PinvokeLib.dll</span><span class="sxs-lookup"><span data-stu-id="83185-146">PinvokeLib.dll</span></span>

<span data-ttu-id="83185-147">Aşağıdaki kod, PInvoke. dll tarafından sunulan kitaplık işlevlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="83185-147">The following code defines the library functions provided by Pinvoke.dll.</span></span> <span data-ttu-id="83185-148">Bu bölümde açıklanan birçok örnek, bu kitaplığı çağırır.</span><span class="sxs-lookup"><span data-stu-id="83185-148">Many samples described in this section call this library.</span></span>

### <a name="example"></a><span data-ttu-id="83185-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="83185-149">Example</span></span>

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
