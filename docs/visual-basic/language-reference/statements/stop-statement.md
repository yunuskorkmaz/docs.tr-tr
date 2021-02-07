---
description: 'Daha fazla bilgi edinin: stop deyimleri (Visual Basic)'
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
ms.openlocfilehash: 1e25eb88d1b85f38a53023dfb7dfbc877f498e5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741087"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="8d626-103">Stop Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d626-103">Stop Statement (Visual Basic)</span></span>

<span data-ttu-id="8d626-104">Yürütmeyi askıya alır.</span><span class="sxs-lookup"><span data-stu-id="8d626-104">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d626-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8d626-105">Syntax</span></span>  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="8d626-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d626-106">Remarks</span></span>  

 <span data-ttu-id="8d626-107">`Stop`Çalışmayı askıya almak için deyimleri yordamların herhangi bir yerinde yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d626-107">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="8d626-108">İfadesinin kullanılması `Stop` kodda bir kesme noktası ayarlamaya benzerdir.</span><span class="sxs-lookup"><span data-stu-id="8d626-108">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="8d626-109">`Stop`İfade yürütmeyi askıya alır, ancak farklı olarak, `End` derlenmiş bir çalıştırılabilir (. exe) dosyasında karşılaşılmadığı takdirde herhangi bir dosyayı kapatmaz veya hiçbir değişkeni temizlemez.</span><span class="sxs-lookup"><span data-stu-id="8d626-109">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d626-110">`Stop`Tümleşik geliştirme ortamı (IDE) dışında çalışan kodda deyime karşılaşılırsa, hata ayıklayıcı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8d626-110">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="8d626-111">Bu, kodun hata ayıklama veya perakende modunda derlenmesinden bağımsız olarak geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8d626-111">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d626-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d626-112">Example</span></span>  

 <span data-ttu-id="8d626-113">Bu örnek, `Stop` döngüsü aracılığıyla her yineleme için yürütmeyi askıya almak üzere ifadesini kullanır `For...Next` .</span><span class="sxs-lookup"><span data-stu-id="8d626-113">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="8d626-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d626-114">See also</span></span>

- [<span data-ttu-id="8d626-115">End ekstresi</span><span class="sxs-lookup"><span data-stu-id="8d626-115">End Statement</span></span>](end-statement.md)
