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
ms.openlocfilehash: a712414163446606cbc93154bc821d3b1166fe8f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800092"
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a><span data-ttu-id="1997d-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1997d-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method</span></span>

<span data-ttu-id="1997d-103">[.NET Framework 4.5.1 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="1997d-103">[Supported in the .NET Framework 4.5.1 and later versions]</span></span>

<span data-ttu-id="1997d-104">Belirtilen akışı rasgele erişim akışına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1997d-104">Converts the specified stream to a random access stream.</span></span>

<span data-ttu-id="1997d-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType> 
 **derleme:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span><span class="sxs-lookup"><span data-stu-id="1997d-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType>
**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span></span>

## <a name="syntax"></a><span data-ttu-id="1997d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1997d-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="1997d-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1997d-107">Parameters</span></span>

`stream`

<span data-ttu-id="1997d-108">Türü: <xref:System.IO.Stream?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1997d-108">Type: <xref:System.IO.Stream?displayProperty=nameWithType></span></span>  
<span data-ttu-id="1997d-109">Dönüştürülecek akış.</span><span class="sxs-lookup"><span data-stu-id="1997d-109">The stream to convert.</span></span>

## <a name="return-value"></a><span data-ttu-id="1997d-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1997d-110">Return Value</span></span>

<span data-ttu-id="1997d-111">Türü: <xref:Windows.Storage.Streams.RandomAccessStream></span><span class="sxs-lookup"><span data-stu-id="1997d-111">Type: <xref:Windows.Storage.Streams.RandomAccessStream></span></span>  
<span data-ttu-id="1997d-112">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] dönüştürülmüş akımı temsil rasgele erişim akışı.</span><span class="sxs-lookup"><span data-stu-id="1997d-112">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.</span></span>

## <a name="exceptions"></a><span data-ttu-id="1997d-113">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="1997d-113">Exceptions</span></span>

|<span data-ttu-id="1997d-114">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="1997d-114">Exception</span></span>|<span data-ttu-id="1997d-115">Koşul</span><span class="sxs-lookup"><span data-stu-id="1997d-115">Condition</span></span>|
|---------------|---------------|
|<xref:System.NotSupportedException>|<span data-ttu-id="1997d-116">Dönüştürülecek akış, aramayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1997d-116">The stream to convert does not support seeking.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1997d-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1997d-117">Remarks</span></span>

<span data-ttu-id="1997d-118">Bu genişletme yöntemi yalnızca Windows Mağazası uygulamaları geliştirirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1997d-118">This extension method is available only when you develop Windows Store apps.</span></span> <span data-ttu-id="1997d-119">Bu yöntem Windows Mağazası uygulamalarında akışlarla çalışmak için uygun bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="1997d-119">This method provides a convenient way of working with streams in Windows Store apps.</span></span> <span data-ttu-id="1997d-120">Dönüştürmek istediğiniz .NET Framework akışının aramayı desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="1997d-120">The .NET Framework stream you want to convert must support seeking.</span></span> <span data-ttu-id="1997d-121">Daha fazla bilgi için <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1997d-121">For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1997d-122">Bu API, .NET Framework 4.5.1 ve sonraki sürümlerde, ancak 4.5 sürümünde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1997d-122">This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.</span></span>

## <a name="version-information"></a><span data-ttu-id="1997d-123">Sürüm Bilgileri</span><span class="sxs-lookup"><span data-stu-id="1997d-123">Version Information</span></span>

<span data-ttu-id="1997d-124">**Windows Store uygulamaları için .NET**</span><span class="sxs-lookup"><span data-stu-id="1997d-124">**.NET for Windows Store apps**</span></span>

<span data-ttu-id="1997d-125">Desteklendiği sürüm: Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="1997d-125">Supported in: Windows 8.1</span></span>

## <a name="see-also"></a><span data-ttu-id="1997d-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1997d-126">See Also</span></span>

<span data-ttu-id="1997d-127">[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions(v=vs.110).aspx)</span><span class="sxs-lookup"><span data-stu-id="1997d-127">[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions(v=vs.110).aspx)</span></span>  
[<span data-ttu-id="1997d-128">Nasıl yapılır: .NET Framework Akışları ile Windows Çalışma Zamanı Akışları Arasında Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="1997d-128">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  