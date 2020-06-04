---
title: COM sınıfından türetilmiş yönetilen sınıflar, geç bağlantılı olarak çağrılamaz.
ms.date: 07/20/2015
f1_keywords:
- vbrLateboundCallToInheritedComClass
ms.assetid: 7bc16e84-8d29-4f8e-bc4f-002c65c71099
ms.openlocfilehash: 401cb5d7194cbef616c87d59e5b1ed7f923fe6f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402128"
---
# <a name="managed-classes-derived-from-a-com-class-cannot-be-called-late-bound"></a><span data-ttu-id="a360b-102">COM sınıfından türetilmiş yönetilen sınıflar, geç bağlantılı olarak çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="a360b-102">Managed classes derived from a COM class cannot be called late-bound.</span></span>

<span data-ttu-id="a360b-103">COM sınıfından türetilmiş yönetilen bir sınıfa geç bağlantılı bir çağrı yapmaya çalıştınız; Bu tür çağrılar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a360b-103">You attempted to make a late-bound call to a managed class derived from a COM Class; such calls are not supported.</span></span>

## <a name="to-correct-the-problem"></a><span data-ttu-id="a360b-104">Sorunu gidermek için</span><span class="sxs-lookup"><span data-stu-id="a360b-104">To correct the problem</span></span>

<span data-ttu-id="a360b-105">Çağrıyı erken bağlantılı hale getirin.</span><span class="sxs-lookup"><span data-stu-id="a360b-105">Make the call early bound.</span></span>

## <a name="see-also"></a><span data-ttu-id="a360b-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a360b-106">See also</span></span>

- [<span data-ttu-id="a360b-107">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="a360b-107">Error Types</span></span>](../programming-guide/language-features/error-types.md)
