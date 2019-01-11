---
title: SqlStreamChars.Write (Char [], Int32, Int32) yöntemi (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: dd9bb691f6d07f4875d684eef76d6329667003af
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221914"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="06506-102">SqlStreamChars.Write (Char [], Int32, Int32) yöntemi</span><span class="sxs-lookup"><span data-stu-id="06506-102">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="06506-103">Türetilen bir sınıfta geçersiz kılındığında, geçerli akışa bir karakter dizisi yazar ve geçerli konumu bu akışın içinde yazılan karakter sayısına göre ilerletir.</span><span class="sxs-lookup"><span data-stu-id="06506-103">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="06506-104">Bu yöntemi içeren derlemenin SQLAccess.dll bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="06506-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="06506-105">Bu, SQL Server tarafından kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="06506-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="06506-106">Diğer veritabanları için veritabanı tarafından sağlanan barındırma mekanizmasına kullanın.</span><span class="sxs-lookup"><span data-stu-id="06506-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="06506-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06506-107">Parameters</span></span>

`buffer`  
<span data-ttu-id="06506-108">Yazılacak karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="06506-108">A char array to write.</span></span>

`offset`  
<span data-ttu-id="06506-109">Kaynağa göre bir uzaklık.</span><span class="sxs-lookup"><span data-stu-id="06506-109">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="06506-110">Geçerli akışa yazılacak karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="06506-110">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="06506-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06506-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="06506-112">`SqlStreamChars.Write` Yöntemi private olduğuna ve kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="06506-112">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="06506-113">Microsoft hiçbir koşulda, bir üretim uygulamasında bu alanı kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="06506-113">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="06506-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06506-114">Requirements</span></span>

<span data-ttu-id="06506-115">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="06506-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="06506-116">**Derleme:** System.Data (içinde System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="06506-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="06506-117">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="06506-117">**.NET Framework versions:** Available since 2.0.</span></span>