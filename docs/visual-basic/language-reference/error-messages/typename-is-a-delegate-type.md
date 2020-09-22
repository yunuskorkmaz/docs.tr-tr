---
title: "'<typename>' bir temsilci türü değil"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 4cc0a1221dcf65aa2a16fd7d82568c8544f27fdb
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875078"
---
# <a name="typename-is-a-delegate-type"></a><span data-ttu-id="2d5da-102">'\<typename>' bir temsilci türü değil</span><span class="sxs-lookup"><span data-stu-id="2d5da-102">'\<typename>' is a delegate type</span></span>

<span data-ttu-id="2d5da-103">' \<typename> ' bir temsilci türüdür.</span><span class="sxs-lookup"><span data-stu-id="2d5da-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="2d5da-104">Temsilci oluşturma, bağımsız değişken listesi olarak yalnızca tek bir AddressOf ifadesine izin veriyor.</span><span class="sxs-lookup"><span data-stu-id="2d5da-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="2d5da-105">Genellikle bir AddressOf ifadesi, temsilci oluşturma yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2d5da-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="2d5da-106">`New`Temsilci sınıfının bir örneğini oluşturan yan tümce, temsilci oluşturucusuna geçersiz bir bağımsız değişken listesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d5da-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="2d5da-107">`AddressOf`Yeni bir temsilci örneği oluştururken yalnızca tek bir ifade sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d5da-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="2d5da-108">Bu hata, birden fazla bağımsız değişken geçirirseniz veya geçerli bir ifade olmayan tek bir bağımsız değişken geçirirseniz, temsilci oluşturucusuna herhangi bir bağımsız değişken geçirmezseniz oluşabilir `AddressOf` .</span><span class="sxs-lookup"><span data-stu-id="2d5da-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="2d5da-109">**Hata kimliği:** BC32008</span><span class="sxs-lookup"><span data-stu-id="2d5da-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2d5da-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2d5da-110">To correct this error</span></span>  
  
- <span data-ttu-id="2d5da-111">`AddressOf`Yan tümcesindeki Delegate sınıfı için bağımsız değişken listesinde tek bir ifade kullanın `New` .</span><span class="sxs-lookup"><span data-stu-id="2d5da-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d5da-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d5da-112">See also</span></span>

- [<span data-ttu-id="2d5da-113">New Işleci</span><span class="sxs-lookup"><span data-stu-id="2d5da-113">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="2d5da-114">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="2d5da-114">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="2d5da-115">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="2d5da-115">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="2d5da-116">Nasıl yapılır: Temsilci Yöntemi Çağırma</span><span class="sxs-lookup"><span data-stu-id="2d5da-116">How to: Invoke a Delegate Method</span></span>](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
