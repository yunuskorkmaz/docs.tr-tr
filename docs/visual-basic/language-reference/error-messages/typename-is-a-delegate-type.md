---
title: "'<typename>' bir temsilci türü değil"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: dcb52188c53b38ac14de0002b5212bb33c9f7203
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161783"
---
# <a name="bc32008-typename-is-a-delegate-type"></a><span data-ttu-id="4a2e1-102">BC32008: ' \<typename> ' bir temsilci türü</span><span class="sxs-lookup"><span data-stu-id="4a2e1-102">BC32008: '\<typename>' is a delegate type</span></span>

<span data-ttu-id="4a2e1-103">' \<typename> ' bir temsilci türüdür.</span><span class="sxs-lookup"><span data-stu-id="4a2e1-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="4a2e1-104">Temsilci oluşturma, bağımsız değişken listesi olarak yalnızca tek bir AddressOf ifadesine izin veriyor.</span><span class="sxs-lookup"><span data-stu-id="4a2e1-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="4a2e1-105">Genellikle bir AddressOf ifadesi, temsilci oluşturma yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a2e1-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>

 <span data-ttu-id="4a2e1-106">`New`Temsilci sınıfının bir örneğini oluşturan yan tümce, temsilci oluşturucusuna geçersiz bir bağımsız değişken listesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a2e1-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>

 <span data-ttu-id="4a2e1-107">`AddressOf`Yeni bir temsilci örneği oluştururken yalnızca tek bir ifade sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a2e1-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>

 <span data-ttu-id="4a2e1-108">Bu hata, birden fazla bağımsız değişken geçirirseniz veya geçerli bir ifade olmayan tek bir bağımsız değişken geçirirseniz, temsilci oluşturucusuna herhangi bir bağımsız değişken geçirmezseniz oluşabilir `AddressOf` .</span><span class="sxs-lookup"><span data-stu-id="4a2e1-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>

 <span data-ttu-id="4a2e1-109">**Hata kimliği:** BC32008</span><span class="sxs-lookup"><span data-stu-id="4a2e1-109">**Error ID:** BC32008</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="4a2e1-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4a2e1-110">To correct this error</span></span>

- <span data-ttu-id="4a2e1-111">`AddressOf`Yan tümcesindeki Delegate sınıfı için bağımsız değişken listesinde tek bir ifade kullanın `New` .</span><span class="sxs-lookup"><span data-stu-id="4a2e1-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a2e1-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a2e1-112">See also</span></span>

- [<span data-ttu-id="4a2e1-113">New Işleci</span><span class="sxs-lookup"><span data-stu-id="4a2e1-113">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="4a2e1-114">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="4a2e1-114">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="4a2e1-115">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="4a2e1-115">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="4a2e1-116">Nasıl yapılır: Temsilci Yöntemi Çağırma</span><span class="sxs-lookup"><span data-stu-id="4a2e1-116">How to: Invoke a Delegate Method</span></span>](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
