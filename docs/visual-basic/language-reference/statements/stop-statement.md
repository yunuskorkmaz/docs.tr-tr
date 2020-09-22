---
title: Stop Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: c9226ccaea9a0709a9d6a49900f69cb9ac9e1dbe
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871739"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="729bd-102">Stop Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="729bd-102">Stop Statement (Visual Basic)</span></span>

<span data-ttu-id="729bd-103">Yürütmeyi askıya alır.</span><span class="sxs-lookup"><span data-stu-id="729bd-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="729bd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="729bd-104">Syntax</span></span>  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="729bd-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="729bd-105">Remarks</span></span>  

 <span data-ttu-id="729bd-106">`Stop`Çalışmayı askıya almak için deyimleri yordamların herhangi bir yerinde yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="729bd-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="729bd-107">İfadesinin kullanılması `Stop` kodda bir kesme noktası ayarlamaya benzerdir.</span><span class="sxs-lookup"><span data-stu-id="729bd-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="729bd-108">`Stop`İfade yürütmeyi askıya alır, ancak farklı olarak, `End` derlenmiş bir çalıştırılabilir (. exe) dosyasında karşılaşılmadığı takdirde herhangi bir dosyayı kapatmaz veya hiçbir değişkeni temizlemez.</span><span class="sxs-lookup"><span data-stu-id="729bd-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="729bd-109">`Stop`Tümleşik geliştirme ortamı (IDE) dışında çalışan kodda deyime karşılaşılırsa, hata ayıklayıcı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="729bd-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="729bd-110">Bu, kodun hata ayıklama veya perakende modunda derlenmesinden bağımsız olarak geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="729bd-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="729bd-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="729bd-111">Example</span></span>  

 <span data-ttu-id="729bd-112">Bu örnek, `Stop` döngüsü aracılığıyla her yineleme için yürütmeyi askıya almak üzere ifadesini kullanır `For...Next` .</span><span class="sxs-lookup"><span data-stu-id="729bd-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="729bd-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="729bd-113">See also</span></span>

- [<span data-ttu-id="729bd-114">End ekstresi</span><span class="sxs-lookup"><span data-stu-id="729bd-114">End Statement</span></span>](end-statement.md)
