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
ms.openlocfilehash: d5dd2829a9a00f869af3d7f370f99361979b8106
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758800"
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a><span data-ttu-id="d2ba6-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2ba6-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method</span></span>

<span data-ttu-id="d2ba6-103">[.NET Framework 4.5.1 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="d2ba6-103">[Supported in the .NET Framework 4.5.1 and later versions]</span></span>

<span data-ttu-id="d2ba6-104">Belirtilen akışı rasgele erişim akışına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d2ba6-104">Converts the specified stream to a random access stream.</span></span>

<span data-ttu-id="d2ba6-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType>
**Derleme:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span><span class="sxs-lookup"><span data-stu-id="d2ba6-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType>
**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span></span>

## <a name="syntax"></a><span data-ttu-id="d2ba6-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2ba6-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="d2ba6-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d2ba6-107">Parameters</span></span>

`stream`

<span data-ttu-id="d2ba6-108">Türü: <xref:System.IO.Stream?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d2ba6-108">Type: <xref:System.IO.Stream?displayProperty=nameWithType></span></span>  
<span data-ttu-id="d2ba6-109">Dönüştürülecek akış.</span><span class="sxs-lookup"><span data-stu-id="d2ba6-109">The stream to convert.</span></span>

## <a name="return-value"></a><span data-ttu-id="d2ba6-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d2ba6-110">Return Value</span></span>

<span data-ttu-id="d2ba6-111">Türü: <xref:Windows.Storage.Streams.RandomAccessStream></span><span class="sxs-lookup"><span data-stu-id="d2ba6-111">Type: <xref:Windows.Storage.Streams.RandomAccessStream></span></span>  
<span data-ttu-id="d2ba6-112">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] dönüştürülmüş akımı temsil rasgele erişim akışı.</span><span class="sxs-lookup"><span data-stu-id="d2ba6-112">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.</span></span>

## <a name="exceptions"></a><span data-ttu-id="d2ba6-113">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="d2ba6-113">Exceptions</span></span>

|<span data-ttu-id="d2ba6-114">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="d2ba6-114">Exception</span></span>|<span data-ttu-id="d2ba6-115">Koşul</span><span class="sxs-lookup"><span data-stu-id="d2ba6-115">Condition</span></span>|
|---------------|---------------|
|<xref:System.NotSupportedException>|<span data-ttu-id="d2ba6-116">Dönüştürülecek akış, aramayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d2ba6-116">The stream to convert does not support seeking.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d2ba6-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2ba6-117">Remarks</span></span>

<span data-ttu-id="d2ba6-118">Bu genişletme yöntemi yalnızca Windows Mağazası uygulamaları geliştirirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2ba6-118">This extension method is available only when you develop Windows Store apps.</span></span> <span data-ttu-id="d2ba6-119">Bu yöntem Windows Mağazası uygulamalarında akışlarla çalışmak için uygun bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2ba6-119">This method provides a convenient way of working with streams in Windows Store apps.</span></span> <span data-ttu-id="d2ba6-120">Dönüştürmek istediğiniz .NET Framework akışının aramayı desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="d2ba6-120">The .NET Framework stream you want to convert must support seeking.</span></span> <span data-ttu-id="d2ba6-121">Daha fazla bilgi için <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2ba6-121">For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d2ba6-122">Bu API, .NET Framework 4.5.1 ve sonraki sürümlerde, ancak 4.5 sürümünde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d2ba6-122">This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.</span></span>

## <a name="version-information"></a><span data-ttu-id="d2ba6-123">Sürüm Bilgileri</span><span class="sxs-lookup"><span data-stu-id="d2ba6-123">Version Information</span></span>

<span data-ttu-id="d2ba6-124">**Windows Store uygulamaları için .NET**</span><span class="sxs-lookup"><span data-stu-id="d2ba6-124">**.NET for Windows Store apps**</span></span>

<span data-ttu-id="d2ba6-125">Desteklenir: Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d2ba6-125">Supported in: Windows 8.1</span></span>

## <a name="see-also"></a><span data-ttu-id="d2ba6-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2ba6-126">See also</span></span>

- [<span data-ttu-id="d2ba6-127">Nasıl yapılır: .NET Framework akışları ve Windows çalışma zamanı akışları arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d2ba6-127">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
