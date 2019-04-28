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
ms.openlocfilehash: 3cb310dc6d786c3c7711f4c194c6623324c777dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642873"
---
# <a name="marshaling-data-with-platform-invoke"></a><span data-ttu-id="541ad-102">Platform Çağırma ile Veri Sıralama</span><span class="sxs-lookup"><span data-stu-id="541ad-102">Marshaling Data with Platform Invoke</span></span>

<span data-ttu-id="541ad-103">Yönetilmeyen bir kitaplığından dışa aktarılan işlevleri çağırmak için bir .NET Framework uygulaması yönetilmeyen işlev temsil eden yönetilen kodda bir işlev prototipi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="541ad-103">To call functions exported from an unmanaged library, a .NET Framework application requires a function prototype in managed code that represents the unmanaged function.</span></span> <span data-ttu-id="541ad-104">Platform sağlayan bir prototip oluşturmak için doğru veri sıralamakta çağırmak, aşağıdakileri yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="541ad-104">To create a prototype that enables platform invoke to marshal data correctly, you must do the following:</span></span>

- <span data-ttu-id="541ad-105">Uygulama <xref:System.Runtime.InteropServices.DllImportAttribute> statik işlev veya yöntem yönetilen kodda özniteliği.</span><span class="sxs-lookup"><span data-stu-id="541ad-105">Apply the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to the static function or method in managed code.</span></span>

- <span data-ttu-id="541ad-106">Yönetilmeyen veri türleri için yönetilen veri türlerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="541ad-106">Substitute managed data types for unmanaged data types.</span></span>

<span data-ttu-id="541ad-107">Yönetilmeyen bir işlev ile sağlanan belgelere özniteliği, isteğe bağlı alanları ile uygulama ve yönetilmeyen türleri için yönetilen veri türlerini değiştirerek bir eşdeğer yönetilen prototip oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="541ad-107">You can use the documentation supplied with an unmanaged function to construct an equivalent managed prototype by applying the attribute with its optional fields and substituting managed data types for unmanaged types.</span></span> <span data-ttu-id="541ad-108">Uygulama hakkında yönergeler için <xref:System.Runtime.InteropServices.DllImportAttribute>, bkz: [yönetilmeyen DLL işlevlerini kullanma](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="541ad-108">For instructions about how to apply the <xref:System.Runtime.InteropServices.DllImportAttribute>, see [Consuming Unmanaged DLL Functions](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).</span></span>

<span data-ttu-id="541ad-109">Bu bölümde, bağımsız değişkenleri geçirme ve yönetilmeyen kitaplıkları tarafından dışarı aktarılan İşlevler'den dönüş değerleri almak için Yönetilen işlev prototipleri oluşturma işlemini gösteren örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="541ad-109">This section provides samples that demonstrate how to create managed function prototypes for passing arguments to and receiving return values from functions exported by unmanaged libraries.</span></span> <span data-ttu-id="541ad-110">Örnekleri de ne zaman kullanılacağını göstermek <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği ve <xref:System.Runtime.InteropServices.Marshal> veri açıkça sıralamakta sınıfı.</span><span class="sxs-lookup"><span data-stu-id="541ad-110">The samples also demonstrate when to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute and the <xref:System.Runtime.InteropServices.Marshal> class to explicitly marshal data.</span></span>

## <a name="platform-invoke-data-types"></a><span data-ttu-id="541ad-111">Platform çağırma veri türleri</span><span class="sxs-lookup"><span data-stu-id="541ad-111">Platform invoke data types</span></span>

<span data-ttu-id="541ad-112">Aşağıdaki tabloda, Windows API'ları ve C-stili İşlevler'de kullanılan veri türlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="541ad-112">The following table lists data types used in the Windows APIs and C-style functions.</span></span> <span data-ttu-id="541ad-113">Bu veri türlerini parametreler ve dönüş değerleri işlevleri birçok yönetilmeyen kitaplıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="541ad-113">Many unmanaged libraries contain functions that pass these data types as parameters and return values.</span></span> <span data-ttu-id="541ad-114">Üçüncü sütunda, karşılık gelen .NET Framework yerleşik değer türünde veya yönetilen kodda kullanan sınıf listeler.</span><span class="sxs-lookup"><span data-stu-id="541ad-114">The third column lists the corresponding .NET Framework built-in value type or class that you use in managed code.</span></span> <span data-ttu-id="541ad-115">Bazı durumlarda tabloda listelenen tür için aynı boyutta bir tür yerine kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="541ad-115">In some cases, you can substitute a type of the same size for the type listed in the table.</span></span>

|<span data-ttu-id="541ad-116">Windows API'lerindeki yönetilmeyen tür</span><span class="sxs-lookup"><span data-stu-id="541ad-116">Unmanaged type in Windows APIs</span></span>|<span data-ttu-id="541ad-117">Yönetilmeyen C dil türü</span><span class="sxs-lookup"><span data-stu-id="541ad-117">Unmanaged C language type</span></span>|<span data-ttu-id="541ad-118">Yönetilen tür</span><span class="sxs-lookup"><span data-stu-id="541ad-118">Managed type</span></span>|<span data-ttu-id="541ad-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="541ad-119">Description</span></span>|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|<span data-ttu-id="541ad-120">Bir değer döndürmeyen bir işlev uygulandı.</span><span class="sxs-lookup"><span data-stu-id="541ad-120">Applied to a function that does not return a value.</span></span>|
|`HANDLE`|`void *`|<span data-ttu-id="541ad-121"><xref:System.IntPtr?displayProperty=nameWithType> veya <xref:System.UIntPtr?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="541ad-121"><xref:System.IntPtr?displayProperty=nameWithType> or <xref:System.UIntPtr?displayProperty=nameWithType></span></span>|<span data-ttu-id="541ad-122">32 bit 32-bit Windows işletim sistemlerine, 64 bit Windows işletim sistemlerinde 64 bit.</span><span class="sxs-lookup"><span data-stu-id="541ad-122">32 bits on 32-bit Windows operating systems, 64 bits on 64-bit Windows operating systems.</span></span>|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="541ad-123">8 bit</span><span class="sxs-lookup"><span data-stu-id="541ad-123">8 bits</span></span>|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="541ad-124">16 bit</span><span class="sxs-lookup"><span data-stu-id="541ad-124">16 bits</span></span>|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="541ad-125">16 bit</span><span class="sxs-lookup"><span data-stu-id="541ad-125">16 bits</span></span>|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="541ad-126">32 bit</span><span class="sxs-lookup"><span data-stu-id="541ad-126">32 bits</span></span>|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="541ad-127">32 bit</span><span class="sxs-lookup"><span data-stu-id="541ad-127">32 bits</span></span>|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="541ad-128">32 bit</span><span class="sxs-lookup"><span data-stu-id="541ad-128">32 bits</span></span>|
|`BOOL`|`long`|<span data-ttu-id="541ad-129"><xref:System.Boolean?displayProperty=nameWithType> veya <xref:System.Int32?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="541ad-129"><xref:System.Boolean?displayProperty=nameWithType> or <xref:System.Int32?displayProperty=nameWithType></span></span>|<span data-ttu-id="541ad-130">32 bit</span><span class="sxs-lookup"><span data-stu-id="541ad-130">32 bits</span></span>|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="541ad-131">32 bit</span><span class="sxs-lookup"><span data-stu-id="541ad-131">32 bits</span></span>|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="541ad-132">32 bit</span><span class="sxs-lookup"><span data-stu-id="541ad-132">32 bits</span></span>|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="541ad-133">ANSI ile işaretleme.</span><span class="sxs-lookup"><span data-stu-id="541ad-133">Decorate with ANSI.</span></span>|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="541ad-134">Unicode süslemek.</span><span class="sxs-lookup"><span data-stu-id="541ad-134">Decorate with Unicode.</span></span>|
|`LPSTR`|`char *`|<span data-ttu-id="541ad-135"><xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="541ad-135"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="541ad-136">ANSI ile işaretleme.</span><span class="sxs-lookup"><span data-stu-id="541ad-136">Decorate with ANSI.</span></span>|
|`LPCSTR`|`const char *`|<span data-ttu-id="541ad-137"><xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="541ad-137"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="541ad-138">ANSI ile işaretleme.</span><span class="sxs-lookup"><span data-stu-id="541ad-138">Decorate with ANSI.</span></span>|
|`LPWSTR`|`wchar_t *`|<span data-ttu-id="541ad-139"><xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="541ad-139"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="541ad-140">Unicode süslemek.</span><span class="sxs-lookup"><span data-stu-id="541ad-140">Decorate with Unicode.</span></span>|
|`LPCWSTR`|`const wchar_t *`|<span data-ttu-id="541ad-141"><xref:System.String?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="541ad-141"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="541ad-142">Unicode süslemek.</span><span class="sxs-lookup"><span data-stu-id="541ad-142">Decorate with Unicode.</span></span>|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="541ad-143">32 bit</span><span class="sxs-lookup"><span data-stu-id="541ad-143">32 bits</span></span>|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="541ad-144">64 bit</span><span class="sxs-lookup"><span data-stu-id="541ad-144">64 bits</span></span>|

<span data-ttu-id="541ad-145">Visual Basic'de karşılık gelen türler için C#ve C++ bkz [.NET Framework sınıf kitaplığı giriş](../../standard/class-library-overview.md#system-namespace).</span><span class="sxs-lookup"><span data-stu-id="541ad-145">For corresponding types in Visual Basic, C#, and C++, see the [Introduction to the .NET Framework Class Library](../../standard/class-library-overview.md#system-namespace).</span></span>

## <a name="pinvokelibdll"></a><span data-ttu-id="541ad-146">PinvokeLib.dll</span><span class="sxs-lookup"><span data-stu-id="541ad-146">PinvokeLib.dll</span></span>

<span data-ttu-id="541ad-147">Aşağıdaki kod Pinvoke.dll tarafından sağlanan kitaplık işlevleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="541ad-147">The following code defines the library functions provided by Pinvoke.dll.</span></span> <span data-ttu-id="541ad-148">Çok sayıda Bu bölümde çağrısında bu kitaplığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="541ad-148">Many samples described in this section call this library.</span></span>

### <a name="example"></a><span data-ttu-id="541ad-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="541ad-149">Example</span></span>

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
