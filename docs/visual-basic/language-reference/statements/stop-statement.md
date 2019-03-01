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
ms.openlocfilehash: 590ac27ebab881353a69077aabdf7a2def3396a6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967855"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="eaa53-102">Stop Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eaa53-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="eaa53-103">Yürütmeyi askıya alır.</span><span class="sxs-lookup"><span data-stu-id="eaa53-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaa53-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eaa53-104">Syntax</span></span>  
  
```  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="eaa53-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eaa53-105">Remarks</span></span>  
 <span data-ttu-id="eaa53-106">Koyabilirsiniz `Stop` deyimleri yürütmeyi askıya almak için herhangi bir yordamda.</span><span class="sxs-lookup"><span data-stu-id="eaa53-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="eaa53-107">Kullanarak `Stop` kodda bir kesme noktası ayarlamak ifade benzerdir.</span><span class="sxs-lookup"><span data-stu-id="eaa53-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="eaa53-108">`Stop` Deyimi askıya alır, ancak yürütme `End`, tüm dosyaları kapatın veya desteklemez derlenmiş yürütülebilir (.exe) dosyasında karşılaşılanaa sürece herhangi bir değişkeni temizleyin.</span><span class="sxs-lookup"><span data-stu-id="eaa53-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eaa53-109">Varsa `Stop` deyimi tümleşik geliştirme ortamı (IDE) dışında çalışan kodu ile karşılaşıldı, hata ayıklayıcı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="eaa53-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="eaa53-110">Bu, perakende veya hata ayıklama modunda kod olup olmadığını derlenen bağımsız olarak geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="eaa53-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eaa53-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="eaa53-111">Example</span></span>  
 <span data-ttu-id="eaa53-112">Bu örnekte `Stop` her yineleme için yürütmeyi askıya almak için deyimi `For...Next` döngü.</span><span class="sxs-lookup"><span data-stu-id="eaa53-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="eaa53-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eaa53-113">See also</span></span>
- [<span data-ttu-id="eaa53-114">End Deyimi</span><span class="sxs-lookup"><span data-stu-id="eaa53-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
