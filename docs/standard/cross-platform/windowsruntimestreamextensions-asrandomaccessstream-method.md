---
title: "WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
api_name: System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream
api_location: System.Runtime.WindowsRuntime.dll
ms.assetid: dcc72283-caed-49ee-b45d-ccaf94e97129
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be93ddc0f3bf0a5079f31bfa0ff5caa882342c37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a><span data-ttu-id="36131-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36131-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method</span></span>
<span data-ttu-id="36131-103">[.NET Framework 4.5.1 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="36131-103">[Supported in the .NET Framework 4.5.1 and later versions]</span></span>  
  
 <span data-ttu-id="36131-104">Belirtilen akışı rasgele erişim akışına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="36131-104">Converts the specified stream to a random access stream.</span></span>  
  
 <span data-ttu-id="36131-105">**Namespace:**<xref:System.IO?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="36131-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType></span></span>  
 <span data-ttu-id="36131-106">**Derleme:** System.Runtime.WindowsRuntime (içinde System.Runtime.WindowsRuntime.dll)</span><span class="sxs-lookup"><span data-stu-id="36131-106">**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36131-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36131-107">Syntax</span></span>  
  
```csharp  
[CLSCompliantAttribute(false)]  
public static  IRandomAccessStream AsRandomAccessStream(Stream stream)  
```  
  
```vb  
'Declaration  
<ExtensionAttribute> _  
<CLSCompliantAttribute(False)> _  
Public Shared Function AsRandomAccessStream ( _  
        stream As Stream) As IRandomAccessStream  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36131-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="36131-108">Parameters</span></span>  
 `stream`  
  
 <span data-ttu-id="36131-109">Türü:<xref:System.IO.Stream?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="36131-109">Type: <xref:System.IO.Stream?displayProperty=nameWithType></span></span>  
<span data-ttu-id="36131-110">Dönüştürülecek akış.</span><span class="sxs-lookup"><span data-stu-id="36131-110">The stream to convert.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36131-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="36131-111">Return Value</span></span>  
 <span data-ttu-id="36131-112">Tür: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)</span><span class="sxs-lookup"><span data-stu-id="36131-112">Type: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)</span></span>  
<span data-ttu-id="36131-113">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] dönüştürülen akışı temsil eden rasgele erişim akış.</span><span class="sxs-lookup"><span data-stu-id="36131-113">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="36131-114">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="36131-114">Exceptions</span></span>  
  
|<span data-ttu-id="36131-115">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="36131-115">Exception</span></span>|<span data-ttu-id="36131-116">Koşul</span><span class="sxs-lookup"><span data-stu-id="36131-116">Condition</span></span>|  
|---------------|---------------|  
|<xref:System.NotSupportedException>|<span data-ttu-id="36131-117">Dönüştürülecek akış, aramayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="36131-117">The stream to convert does not support seeking.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36131-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36131-118">Remarks</span></span>  
 <span data-ttu-id="36131-119">Bu genişletme yöntemi yalnızca Windows Mağazası uygulamaları geliştirirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="36131-119">This extension method is available only when you develop Windows Store apps.</span></span> <span data-ttu-id="36131-120">Bu yöntem Windows Mağazası uygulamalarında akışlarla çalışmak için uygun bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="36131-120">This method provides a convenient way of working with streams in Windows Store apps.</span></span> <span data-ttu-id="36131-121">Dönüştürmek istediğiniz .NET Framework Akış aramayı desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="36131-121">The .NET Framework stream you want to convert must support seeking.</span></span> <span data-ttu-id="36131-122">Daha fazla bilgi için bkz: <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="36131-122">For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="36131-123">Bu API, .NET Framework 4.5.1 ve sonraki sürümlerinde, ancak sürüm 4.5 desteklenir.</span><span class="sxs-lookup"><span data-stu-id="36131-123">This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.</span></span>  
  
## <a name="version-information"></a><span data-ttu-id="36131-124">Sürüm Bilgileri</span><span class="sxs-lookup"><span data-stu-id="36131-124">Version Information</span></span>  
 <span data-ttu-id="36131-125">**Windows mağazası uygulamaları için .NET**</span><span class="sxs-lookup"><span data-stu-id="36131-125">**.NET for Windows Store apps**</span></span>  
  
 <span data-ttu-id="36131-126">Desteklendiği sürüm: Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="36131-126">Supported in: Windows 8.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36131-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36131-127">See Also</span></span>  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions`  
 [<span data-ttu-id="36131-128">Nasıl yapılır: .NET Framework akışları ile Windows çalışma zamanı akışları arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="36131-128">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
