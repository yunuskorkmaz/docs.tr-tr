---
title: Stop Deyimi (Visual Basic)
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
ms.openlocfilehash: a617038ec51d98c62b6cf7e3c124c8af01305bac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957615"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="ed76f-102">Stop Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed76f-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="ed76f-103">Yürütmeyi askıya alır.</span><span class="sxs-lookup"><span data-stu-id="ed76f-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed76f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed76f-104">Syntax</span></span>  
  
```  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="ed76f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed76f-105">Remarks</span></span>  
 <span data-ttu-id="ed76f-106">Çalışmayı askıya almak `Stop` için deyimleri yordamların herhangi bir yerinde yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed76f-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="ed76f-107">`Stop` İfadesinin kullanılması kodda bir kesme noktası ayarlamaya benzerdir.</span><span class="sxs-lookup"><span data-stu-id="ed76f-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="ed76f-108">İfade yürütmeyi askıya alır, ancak farklı `End`olarak, derlenmiş bir çalıştırılabilir (. exe) dosyasında karşılaşılmadığı takdirde herhangi bir dosyayı kapatmaz veya hiçbir değişkeni temizlemez. `Stop`</span><span class="sxs-lookup"><span data-stu-id="ed76f-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed76f-109">Tümleşik geliştirme ortamı (IDE) dışında çalışan kodda deyimekarşılaşılırsa,hataayıklayıcıçağrılır.`Stop`</span><span class="sxs-lookup"><span data-stu-id="ed76f-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="ed76f-110">Bu, kodun hata ayıklama veya perakende modunda derlenmesinden bağımsız olarak geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ed76f-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed76f-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed76f-111">Example</span></span>  
 <span data-ttu-id="ed76f-112">Bu örnek, `Stop` `For...Next` döngüsü aracılığıyla her yineleme için yürütmeyi askıya almak üzere ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ed76f-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="ed76f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed76f-113">See also</span></span>

- [<span data-ttu-id="ed76f-114">End Deyimi</span><span class="sxs-lookup"><span data-stu-id="ed76f-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
