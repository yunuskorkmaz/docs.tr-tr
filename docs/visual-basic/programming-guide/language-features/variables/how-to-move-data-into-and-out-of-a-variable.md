---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: bir değişkenin Içine ve dışına veri taşıma (Visual Basic)'
title: 'Nasıl yapılır: Bir Değişkende Veri Ekleme Çıkarma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: e75be83f82a3e1418099375eb52a2d2cc4fdbd18
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481824"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="f651d-103">Nasıl yapılır: Bir Değişkende Veri Ekleme Çıkarma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f651d-103">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>

<span data-ttu-id="f651d-104">Değişken adını atama ifadesinin sol tarafına koyarak bir değişkende bir değer depolursunuz.</span><span class="sxs-lookup"><span data-stu-id="f651d-104">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>

## <a name="putting-data-in-a-variable"></a><span data-ttu-id="f651d-105">Verileri bir değişkene koyma</span><span class="sxs-lookup"><span data-stu-id="f651d-105">Putting Data in a Variable</span></span>

#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="f651d-106">Bir değişkende bir değeri depolamak için</span><span class="sxs-lookup"><span data-stu-id="f651d-106">To store a value in a variable</span></span>

- <span data-ttu-id="f651d-107">Atama ifadesinin sol tarafındaki değişken adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="f651d-107">Use the variable name on the left side of an assignment statement.</span></span>

    <span data-ttu-id="f651d-108">Aşağıdaki örnek, değişkenin değerini ayarlar `alpha` .</span><span class="sxs-lookup"><span data-stu-id="f651d-108">The following example sets the value of the variable `alpha`.</span></span>

    ```vb
    alpha = (beta * 6.27) / (gamma + 2.1)
    ```

    <span data-ttu-id="f651d-109">Atama ifadesinin sağ tarafında oluşturulan değer değişkeninde depolanır.</span><span class="sxs-lookup"><span data-stu-id="f651d-109">The value generated on the right side of the assignment statement is stored in the variable.</span></span>

## <a name="getting-data-from-a-variable"></a><span data-ttu-id="f651d-110">Bir değişkenden veri alma</span><span class="sxs-lookup"><span data-stu-id="f651d-110">Getting Data from a Variable</span></span>

<span data-ttu-id="f651d-111">Değişkenin değerini bir ifadeye değişken adını ekleyerek alırsınız.</span><span class="sxs-lookup"><span data-stu-id="f651d-111">You retrieve a variable's value by including the variable name in an expression.</span></span>

#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="f651d-112">Bir değişkenden değer almak için</span><span class="sxs-lookup"><span data-stu-id="f651d-112">To retrieve a value from a variable</span></span>

- <span data-ttu-id="f651d-113">Bir ifadede değişken adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="f651d-113">Use the variable name in an expression.</span></span> <span data-ttu-id="f651d-114">Bir sabiti, bir sabit veya sabit değer, bir sabit değeri tanımlayan bir ifade dışında herhangi bir yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f651d-114">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>

  <span data-ttu-id="f651d-115">\-veya</span><span class="sxs-lookup"><span data-stu-id="f651d-115">\-or-</span></span>

- <span data-ttu-id="f651d-116">Atama deyimindeki eşittir () işaretinden sonraki değişken adını kullanın `=` .</span><span class="sxs-lookup"><span data-stu-id="f651d-116">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>

  <span data-ttu-id="f651d-117">Aşağıdaki örnek, değişkenin değerini okur `startValue` ve sonra değişkenin değerini `counter` bir ifadede kullanır.</span><span class="sxs-lookup"><span data-stu-id="f651d-117">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>

  ```vb
  counter = startValue
  cellValue = (counter + 5) ^ 2
  ```

  <span data-ttu-id="f651d-118">Değişkenin değeri yalnızca bir sabit olarak ifade edilir ve sonra atama deyiminin sol tarafındaki değişken veya özellikte saklanır.</span><span class="sxs-lookup"><span data-stu-id="f651d-118">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="f651d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f651d-119">See also</span></span>

- [<span data-ttu-id="f651d-120">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="f651d-120">Variables</span></span>](index.md)
- [<span data-ttu-id="f651d-121">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="f651d-121">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="f651d-122">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f651d-122">Object Variables</span></span>](object-variables.md)
