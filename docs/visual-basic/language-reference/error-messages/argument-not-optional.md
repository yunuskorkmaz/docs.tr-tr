---
description: 'Hakkında daha fazla bilgi edinin: bağımsız değişken isteğe bağlı değil (Visual Basic)'
title: Bağımsız değişken isteğe bağlı değil
ms.date: 07/20/2015
f1_keywords:
- vbrID449
ms.assetid: 76e7bcf3-24ed-4cd5-945b-b98f1c76944b
ms.openlocfilehash: 3683f07174b980f6ceebf42151658a5be4615310
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797165"
---
# <a name="argument-not-optional-visual-basic"></a><span data-ttu-id="14ccb-103">Bağımsız değişken isteğe bağlı değil (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14ccb-103">Argument not optional (Visual Basic)</span></span>

<span data-ttu-id="14ccb-104">Bağımsız değişkenlerin sayısı ve türleri beklenenlerle aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="14ccb-104">The number and types of arguments must match those expected.</span></span> <span data-ttu-id="14ccb-105">Yanlış sayıda bağımsız değişken var veya atlanmış bir bağımsız değişken isteğe bağlı değil.</span><span class="sxs-lookup"><span data-stu-id="14ccb-105">Either there is an incorrect number of arguments, or an omitted argument is not optional.</span></span> <span data-ttu-id="14ccb-106">Bağımsız değişken, yalnızca yordam tanımında bildirilirse Kullanıcı tanımlı yordama yapılan çağrıdan atlanabilir `Optional` .</span><span class="sxs-lookup"><span data-stu-id="14ccb-106">An argument can only be omitted from a call to a user-defined procedure if it was declared `Optional` in the procedure definition.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="14ccb-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="14ccb-107">To correct this error</span></span>  
  
1. <span data-ttu-id="14ccb-108">Tüm gerekli bağımsız değişkenleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="14ccb-108">Supply all necessary arguments.</span></span>  
  
2. <span data-ttu-id="14ccb-109">Atlanan bağımsız değişkenlerin isteğe bağlı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="14ccb-109">Make sure omitted arguments are optional.</span></span> <span data-ttu-id="14ccb-110">Aksi takdirde, çağrın bağımsız değişkenini sağlayın ya da parametreyi `Optional` tanımda bildirin.</span><span class="sxs-lookup"><span data-stu-id="14ccb-110">If they are not, either supply the argument in the call, or declare the parameter `Optional` in the definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14ccb-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14ccb-111">See also</span></span>

- [<span data-ttu-id="14ccb-112">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="14ccb-112">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
