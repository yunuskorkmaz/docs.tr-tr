---
title: Tür bağımsız değişkenleri temsilciden gösterilemedi
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: f7937a34ab425da684f892250884d21e020e4c57
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161250"
---
# <a name="bc36564-type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="567cb-102">BC36564: tür bağımsız değişkenleri temsilciden çıkarsanamadı</span><span class="sxs-lookup"><span data-stu-id="567cb-102">BC36564: Type arguments could not be inferred from the delegate</span></span>

<span data-ttu-id="567cb-103">Atama ekstresi `AddressOf` , bir temsilciye genel yordamın adresini atamak için kullanır, ancak genel yordamda herhangi bir tür bağımsız değişkeni sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="567cb-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>

 <span data-ttu-id="567cb-104">Normal olarak, genel bir tür çağırdığınızda, genel türün tanımladığı her tür parametresi için bir tür bağımsız değişkeni sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="567cb-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="567cb-105">Herhangi bir tür bağımsız değişkeni belirtmezseniz, derleyici tür parametrelerine geçirilecek türleri çıkarması için girişimde bulunur.</span><span class="sxs-lookup"><span data-stu-id="567cb-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="567cb-106">Bağlam derleyicinin türleri çıkarması için yeterli bilgi sağlamıyorsa bir hata oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="567cb-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>

 <span data-ttu-id="567cb-107">**Hata kimliği:** BC36564</span><span class="sxs-lookup"><span data-stu-id="567cb-107">**Error ID:** BC36564</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="567cb-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="567cb-108">To correct this error</span></span>

- <span data-ttu-id="567cb-109">İfadedeki genel yordamın tür bağımsız değişkenlerini belirtin `AddressOf` .</span><span class="sxs-lookup"><span data-stu-id="567cb-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>

## <a name="see-also"></a><span data-ttu-id="567cb-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="567cb-110">See also</span></span>

- [<span data-ttu-id="567cb-111">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="567cb-111">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="567cb-112">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="567cb-112">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="567cb-113">Visual Basic'de Genel Yordamlar</span><span class="sxs-lookup"><span data-stu-id="567cb-113">Generic Procedures in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="567cb-114">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="567cb-114">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="567cb-115">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="567cb-115">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
