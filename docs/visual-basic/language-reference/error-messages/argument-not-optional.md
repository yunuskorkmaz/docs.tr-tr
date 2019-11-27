---
title: Bağımsız değişken isteğe bağlı değil
ms.date: 07/20/2015
f1_keywords:
- vbrID449
ms.assetid: 76e7bcf3-24ed-4cd5-945b-b98f1c76944b
ms.openlocfilehash: 043d126b07838f1a98788021048e5f22e3bc42ed
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353910"
---
# <a name="argument-not-optional-visual-basic"></a><span data-ttu-id="a43f8-102">Bağımsız değişken isteğe bağlı değil (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a43f8-102">Argument not optional (Visual Basic)</span></span>

<span data-ttu-id="a43f8-103">Bağımsız değişkenlerin sayısı ve türleri beklenenlerle aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a43f8-103">The number and types of arguments must match those expected.</span></span> <span data-ttu-id="a43f8-104">Yanlış sayıda bağımsız değişken var veya atlanmış bir bağımsız değişken isteğe bağlı değil.</span><span class="sxs-lookup"><span data-stu-id="a43f8-104">Either there is an incorrect number of arguments, or an omitted argument is not optional.</span></span> <span data-ttu-id="a43f8-105">Bir bağımsız değişken, yalnızca yordam tanımında `Optional` bildirilirse, Kullanıcı tanımlı yordama yapılan çağrıdan atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a43f8-105">An argument can only be omitted from a call to a user-defined procedure if it was declared `Optional` in the procedure definition.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a43f8-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a43f8-106">To correct this error</span></span>  
  
1. <span data-ttu-id="a43f8-107">Tüm gerekli bağımsız değişkenleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="a43f8-107">Supply all necessary arguments.</span></span>  
  
2. <span data-ttu-id="a43f8-108">Atlanan bağımsız değişkenlerin isteğe bağlı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a43f8-108">Make sure omitted arguments are optional.</span></span> <span data-ttu-id="a43f8-109">Aksi takdirde, çağrın bağımsız değişkenini sağlayın ya da `Optional` parametre tanımını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a43f8-109">If they are not, either supply the argument in the call, or declare the parameter `Optional` in the definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a43f8-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a43f8-110">See also</span></span>

- [<span data-ttu-id="a43f8-111">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="a43f8-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
