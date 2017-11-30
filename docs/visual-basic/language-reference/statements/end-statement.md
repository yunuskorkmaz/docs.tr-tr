---
title: End Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b692409f2895f5e9b713c57fc35ff2def40bce75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="end-statement"></a><span data-ttu-id="03a89-102">End Deyimi</span><span class="sxs-lookup"><span data-stu-id="03a89-102">End Statement</span></span>
<span data-ttu-id="03a89-103">Yürütme hemen sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="03a89-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03a89-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03a89-104">Syntax</span></span>  
  
```  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="03a89-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03a89-105">Remarks</span></span>  
 <span data-ttu-id="03a89-106">Yerleştireceğiniz `End` çalışmayı durdurmasına tüm uygulama zorlamak için bir yordam herhangi bir yere deyiminde.</span><span class="sxs-lookup"><span data-stu-id="03a89-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="03a89-107">`End`ile açılan dosyaları kapatır bir `Open` deyimi ve uygulamanın tüm değişkenleri temizler.</span><span class="sxs-lookup"><span data-stu-id="03a89-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="03a89-108">Uygulama nesnelerine başvurular bulunduran diğer program yok ve kendi kod hiçbiri çalışıyorsa hemen kapatılır.</span><span class="sxs-lookup"><span data-stu-id="03a89-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03a89-109">`End` Deyimi kod yürütmeyi aniden durdurur ve çağrılamadı `Dispose` veya `Finalize` yöntemi veya başka bir Visual Basic kodu.</span><span class="sxs-lookup"><span data-stu-id="03a89-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="03a89-110">Nesne başvuruları diğer programlar tarafından tutulan geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="03a89-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="03a89-111">Varsa bir `End` deyimi karşılaştı içinde bir `Try` veya `Catch` denetim bloğu değil geçirmek karşılık gelen `Finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="03a89-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="03a89-112">`Stop` Deyimi askıya alır, ancak yürütme `End`, bırakmaz tüm dosyaları kapatın veya bir derlenmiş yürütülebilir dosyanın (.exe) dosyasında karşılaşılan sürece herhangi bir değişkeni temizleyin.</span><span class="sxs-lookup"><span data-stu-id="03a89-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="03a89-113">Çünkü `End` uygulamanızı katılımın olmadan sonlandırır açık olabilecek tüm kaynaklarına yakın düzgün bir şekilde kullanmadan önce aşağı denemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="03a89-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="03a89-114">Açık herhangi bir form uygulamanız varsa, örneğin, bunları denetim ulaştığında önce kapatmalısınız `End` deyimi.</span><span class="sxs-lookup"><span data-stu-id="03a89-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="03a89-115">Kullanmanız gereken `End` gerektiğinde ve yalnızca zaman hemen durdurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="03a89-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="03a89-116">Bir yordam sonlandırmak için normal şekilde ([dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md) ve [çıkış deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)) yalnızca yordamı düzgün bir şekilde kapatın, ancak ayrıca çağıran kodu Kapat düzgün bir şekilde aşağı fırsatı sunmak.</span><span class="sxs-lookup"><span data-stu-id="03a89-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="03a89-117">Örneğin, bir konsol uygulaması kolayca kaldırabilirsiniz `Return` gelen `Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="03a89-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="03a89-118">`End` Deyimi çağrıları <xref:System.Environment.Exit%2A> yöntemi <xref:System.Environment> sınıfını <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="03a89-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="03a89-119"><xref:System.Environment.Exit%2A>sahip olmasını gerektiren `UnmanagedCode` izni.</span><span class="sxs-lookup"><span data-stu-id="03a89-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="03a89-120">Aksi halde bir <xref:System.Security.SecurityException> hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="03a89-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="03a89-121">Bir ek anahtar tarafından izlendiğinde [son \<anahtar sözcüğü > deyimi](../../../visual-basic/language-reference/statements/end-keyword-statement.md) uygun yordamı veya blok tanımını sonuna betimleyen.</span><span class="sxs-lookup"><span data-stu-id="03a89-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="03a89-122">Örneğin, `End Function` tanımını sonlandırır bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="03a89-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03a89-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="03a89-123">Example</span></span>  
 <span data-ttu-id="03a89-124">Aşağıdaki örnek kullanır `End` kullanıcı isterse kod yürütmeyi sonlandırmak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="03a89-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="03a89-125">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="03a89-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="03a89-126">Bu deyim desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="03a89-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a89-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03a89-127">See Also</span></span>  
 <xref:System.Security.Permissions.SecurityPermissionFlag>  
 [<span data-ttu-id="03a89-128">Stop deyimi</span><span class="sxs-lookup"><span data-stu-id="03a89-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [<span data-ttu-id="03a89-129">Son \<anahtar sözcüğü > deyimi</span><span class="sxs-lookup"><span data-stu-id="03a89-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
