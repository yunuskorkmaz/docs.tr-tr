---
title: "Nasıl yapılır: Bir Nesne Değişkeninin Hiçbir Örneğe Başvurmamasını Sağlama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b33aef06300bf35b7138ec5b40747532a77140a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="9ed91-102">Nasıl yapılır: Bir Nesne Değişkeninin Hiçbir Örneğe Başvurmamasını Sağlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ed91-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="9ed91-103">Ayarlayarak bir nesne değişkeninin hiçbir nesne örneğinden ilişkisini [hiçbir şey](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="9ed91-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="9ed91-104">Bir nesne değişkeninin hiçbir nesne örneğinden ilişkisini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="9ed91-104">To disassociate an object variable from any object instance</span></span>  
  
-   <span data-ttu-id="9ed91-105">Değişkeni kümesine `Nothing` atama deyimi içinde.</span><span class="sxs-lookup"><span data-stu-id="9ed91-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="9ed91-106">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="9ed91-106">Robust Programming</span></span>  
 <span data-ttu-id="9ed91-107">Kodunuzu ayarlanmış olan bir nesne değişkeni üyesi erişmeye çalışırsa `Nothing`, <xref:System.NullReferenceException> oluşur.</span><span class="sxs-lookup"><span data-stu-id="9ed91-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="9ed91-108">Bir nesne değişkeni ayarlarsanız `Nothing` sık veya değişkeni başlatılmadı Mümkünse, bu üye erişimleri kapsamak için iyi bir fikirdir bir `Try...Catch...Finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="9ed91-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9ed91-109">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="9ed91-109">.NET Framework Security</span></span>  
 <span data-ttu-id="9ed91-110">Gizli veya hassas veri içeren nesneler için bir nesne değişkeni kullanırsanız, değişkeni ayarlayabileceğiniz `Nothing` zaman, değil etkin olarak ilgilenme Bu nesnelerden biri.</span><span class="sxs-lookup"><span data-stu-id="9ed91-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="9ed91-111">Bu, kötü amaçlı kod veri erişimini olasılığını azaltır.</span><span class="sxs-lookup"><span data-stu-id="9ed91-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed91-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9ed91-112">See Also</span></span>  
 <xref:System.NullReferenceException>  
 [<span data-ttu-id="9ed91-113">Nesne değişkenleri</span><span class="sxs-lookup"><span data-stu-id="9ed91-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="9ed91-114">Nesne değişkeni ataması</span><span class="sxs-lookup"><span data-stu-id="9ed91-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="9ed91-115">Hiçbir şey</span><span class="sxs-lookup"><span data-stu-id="9ed91-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="9ed91-116">Try... Catch... Finally ifadesi</span><span class="sxs-lookup"><span data-stu-id="9ed91-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="9ed91-117">Özel durum sorunlarını giderme: System.NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="9ed91-117">Troubleshooting Exceptions: System.NullReferenceException</span></span>](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
