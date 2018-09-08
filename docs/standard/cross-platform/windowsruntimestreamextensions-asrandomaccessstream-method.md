---
title: WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Yöntemi
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
api_name:
- System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream
api_location:
- System.Runtime.WindowsRuntime.dll
ms.assetid: dcc72283-caed-49ee-b45d-ccaf94e97129
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8935a8c282bbe812ad76ac6d4228c38ab12626a4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193594"
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a><span data-ttu-id="e1f3e-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1f3e-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method</span></span>

<span data-ttu-id="e1f3e-103">[.NET Framework 4.5.1 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="e1f3e-103">[Supported in the .NET Framework 4.5.1 and later versions]</span></span>

<span data-ttu-id="e1f3e-104">Belirtilen akışı rasgele erişim akışına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e1f3e-104">Converts the specified stream to a random access stream.</span></span>

<span data-ttu-id="e1f3e-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType> 
 **derleme:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span><span class="sxs-lookup"><span data-stu-id="e1f3e-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType>
**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1f3e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1f3e-106">Syntax</span></span>

```csharp
[CLSCompliantAttribute(false)]
public static IRandomAccessStream AsRandomAccessStream(Stream stream)
```

```vb
'Declaration
<ExtensionAttribute> _
<CLSCompliantAttribute(False)> _
Public Shared Function AsRandomAccessStream ( _
        stream As Stream) As IRandomAccessStream
```

## <a name="parameters"></a><span data-ttu-id="e1f3e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1f3e-107">Parameters</span></span>

`stream`

<span data-ttu-id="e1f3e-108">Türü: <xref:System.IO.Stream?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e1f3e-108">Type: <xref:System.IO.Stream?displayProperty=nameWithType></span></span>  
<span data-ttu-id="e1f3e-109">Dönüştürülecek akış.</span><span class="sxs-lookup"><span data-stu-id="e1f3e-109">The stream to convert.</span></span>

## <a name="return-value"></a><span data-ttu-id="e1f3e-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e1f3e-110">Return Value</span></span>

<span data-ttu-id="e1f3e-111">Türü: <xref:Windows.Storage.Streams.RandomAccessStream></span><span class="sxs-lookup"><span data-stu-id="e1f3e-111">Type: <xref:Windows.Storage.Streams.RandomAccessStream></span></span>  
<span data-ttu-id="e1f3e-112">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] dönüştürülmüş akımı temsil rasgele erişim akışı.</span><span class="sxs-lookup"><span data-stu-id="e1f3e-112">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.</span></span>

## <a name="exceptions"></a><span data-ttu-id="e1f3e-113">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="e1f3e-113">Exceptions</span></span>

|<span data-ttu-id="e1f3e-114">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="e1f3e-114">Exception</span></span>|<span data-ttu-id="e1f3e-115">Koşul</span><span class="sxs-lookup"><span data-stu-id="e1f3e-115">Condition</span></span>|
|---------------|---------------|
|<xref:System.NotSupportedException>|<span data-ttu-id="e1f3e-116">Dönüştürülecek akış, aramayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e1f3e-116">The stream to convert does not support seeking.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e1f3e-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1f3e-117">Remarks</span></span>

<span data-ttu-id="e1f3e-118">Bu genişletme yöntemi yalnızca Windows Mağazası uygulamaları geliştirirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1f3e-118">This extension method is available only when you develop Windows Store apps.</span></span> <span data-ttu-id="e1f3e-119">Bu yöntem Windows Mağazası uygulamalarında akışlarla çalışmak için uygun bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1f3e-119">This method provides a convenient way of working with streams in Windows Store apps.</span></span> <span data-ttu-id="e1f3e-120">Dönüştürmek istediğiniz .NET Framework akışının aramayı desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="e1f3e-120">The .NET Framework stream you want to convert must support seeking.</span></span> <span data-ttu-id="e1f3e-121">Daha fazla bilgi için <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e1f3e-121">For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1f3e-122">Bu API, .NET Framework 4.5.1 ve sonraki sürümlerde, ancak 4.5 sürümünde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e1f3e-122">This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.</span></span>

## <a name="version-information"></a><span data-ttu-id="e1f3e-123">Sürüm Bilgileri</span><span class="sxs-lookup"><span data-stu-id="e1f3e-123">Version Information</span></span>

<span data-ttu-id="e1f3e-124">**Windows Store uygulamaları için .NET**</span><span class="sxs-lookup"><span data-stu-id="e1f3e-124">**.NET for Windows Store apps**</span></span>

<span data-ttu-id="e1f3e-125">Desteklendiği sürüm: Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="e1f3e-125">Supported in: Windows 8.1</span></span>

## <a name="see-also"></a><span data-ttu-id="e1f3e-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1f3e-126">See also</span></span>

<span data-ttu-id="e1f3e-127">-[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions(v=vs.110).aspx)
-[nasıl yapılır: .NET Framework akışları ile Windows çalışma zamanı akışları arasında dönüştürme](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)</span><span class="sxs-lookup"><span data-stu-id="e1f3e-127">-[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions(v=vs.110).aspx)
-[How to: Convert Between .NET Framework Streams and Windows Runtime Streams](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)</span></span>
