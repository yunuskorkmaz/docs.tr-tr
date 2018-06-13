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
ms.openlocfilehash: 955a3b6a2f7dc1d0e9823ed6d500ab7f7f9fe5b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599141"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="20d2a-102">Stop Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20d2a-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="20d2a-103">Yürütme askıya alır.</span><span class="sxs-lookup"><span data-stu-id="20d2a-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20d2a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20d2a-104">Syntax</span></span>  
  
```  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="20d2a-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20d2a-105">Remarks</span></span>  
 <span data-ttu-id="20d2a-106">Yerleştireceğiniz `Stop` yürütme askıya almak için herhangi bir yere yordamları deyimlerinde.</span><span class="sxs-lookup"><span data-stu-id="20d2a-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="20d2a-107">Kullanarak `Stop` deyimi kodda kesme noktası ayarlama benzer.</span><span class="sxs-lookup"><span data-stu-id="20d2a-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="20d2a-108">`Stop` Deyimi askıya alır, ancak yürütme `End`, bırakmaz tüm dosyaları kapatın veya bir derlenmiş yürütülebilir dosyanın (.exe) dosyasında karşılaşılan sürece herhangi bir değişkeni temizleyin.</span><span class="sxs-lookup"><span data-stu-id="20d2a-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20d2a-109">Varsa `Stop` deyimi tümleşik geliştirme ortamı (IDE) dışında çalışan kodu ile karşılaştı, hata ayıklayıcı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="20d2a-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="20d2a-110">Bu kod hata ayıklama veya perakende modunda olup olmadığını derlenen bağımsız olarak geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="20d2a-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20d2a-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="20d2a-111">Example</span></span>  
 <span data-ttu-id="20d2a-112">Bu örnekte `Stop` yürütme her bir yineleme için askıya almak için deyimi `For...Next` döngü.</span><span class="sxs-lookup"><span data-stu-id="20d2a-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="20d2a-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20d2a-113">See Also</span></span>  
 [<span data-ttu-id="20d2a-114">End Deyimi</span><span class="sxs-lookup"><span data-stu-id="20d2a-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
