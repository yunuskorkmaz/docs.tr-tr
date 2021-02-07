---
description: "Hakkında daha fazla bilgi edinin: BC32008: ' <typename> ' bir temsilci türü"
title: "'<typename>' bir temsilci türü değil"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 72aac48038c433b7938c54e7f1138a5b91bf7689
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675032"
---
# <a name="bc32008-typename-is-a-delegate-type"></a><span data-ttu-id="527ce-103">BC32008: ' \<typename> ' bir temsilci türü</span><span class="sxs-lookup"><span data-stu-id="527ce-103">BC32008: '\<typename>' is a delegate type</span></span>

<span data-ttu-id="527ce-104">' \<typename> ' bir temsilci türüdür.</span><span class="sxs-lookup"><span data-stu-id="527ce-104">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="527ce-105">Temsilci oluşturma, bağımsız değişken listesi olarak yalnızca tek bir AddressOf ifadesine izin veriyor.</span><span class="sxs-lookup"><span data-stu-id="527ce-105">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="527ce-106">Genellikle bir AddressOf ifadesi, temsilci oluşturma yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="527ce-106">Often an AddressOf expression can be used instead of a delegate construction.</span></span>

 <span data-ttu-id="527ce-107">`New`Temsilci sınıfının bir örneğini oluşturan yan tümce, temsilci oluşturucusuna geçersiz bir bağımsız değişken listesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="527ce-107">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>

 <span data-ttu-id="527ce-108">`AddressOf`Yeni bir temsilci örneği oluştururken yalnızca tek bir ifade sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="527ce-108">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>

 <span data-ttu-id="527ce-109">Bu hata, birden fazla bağımsız değişken geçirirseniz veya geçerli bir ifade olmayan tek bir bağımsız değişken geçirirseniz, temsilci oluşturucusuna herhangi bir bağımsız değişken geçirmezseniz oluşabilir `AddressOf` .</span><span class="sxs-lookup"><span data-stu-id="527ce-109">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>

 <span data-ttu-id="527ce-110">**Hata kimliği:** BC32008</span><span class="sxs-lookup"><span data-stu-id="527ce-110">**Error ID:** BC32008</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="527ce-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="527ce-111">To correct this error</span></span>

- <span data-ttu-id="527ce-112">`AddressOf`Yan tümcesindeki Delegate sınıfı için bağımsız değişken listesinde tek bir ifade kullanın `New` .</span><span class="sxs-lookup"><span data-stu-id="527ce-112">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>

## <a name="see-also"></a><span data-ttu-id="527ce-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="527ce-113">See also</span></span>

- [<span data-ttu-id="527ce-114">New Işleci</span><span class="sxs-lookup"><span data-stu-id="527ce-114">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="527ce-115">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="527ce-115">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="527ce-116">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="527ce-116">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="527ce-117">Nasıl yapılır: Temsilci Yöntemi Çağırma</span><span class="sxs-lookup"><span data-stu-id="527ce-117">How to: Invoke a Delegate Method</span></span>](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
