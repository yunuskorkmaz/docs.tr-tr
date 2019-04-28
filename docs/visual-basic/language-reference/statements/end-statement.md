---
title: End deyimi (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 4fc4fd36fb6b057195e9d8a79eb0a5b3ac9ff95c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638148"
---
# <a name="end-statement"></a><span data-ttu-id="77c5f-102">End Deyimi</span><span class="sxs-lookup"><span data-stu-id="77c5f-102">End Statement</span></span>
<span data-ttu-id="77c5f-103">Yürütmeyi hemen sonlanır.</span><span class="sxs-lookup"><span data-stu-id="77c5f-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77c5f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77c5f-104">Syntax</span></span>  
  
```  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="77c5f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77c5f-105">Remarks</span></span>  
 <span data-ttu-id="77c5f-106">Koyabilirsiniz `End` yordamındaki durmaya uygulamanın tamamı zorlamak için her yerden bir.</span><span class="sxs-lookup"><span data-stu-id="77c5f-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="77c5f-107">`End` açılmış neden olan tüm dosyaları kapatır bir `Open` deyimi ve uygulamanın tüm değişkenleri temizler.</span><span class="sxs-lookup"><span data-stu-id="77c5f-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="77c5f-108">Uygulama nesnelerini için başvuru bulunduran başka bir program vardır ve kendi kod hiçbiri çalıştıran hemen kapatır.</span><span class="sxs-lookup"><span data-stu-id="77c5f-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77c5f-109">`End` Deyimi yürütmeyi aniden durdurur ve çağrılamadı `Dispose` veya `Finalize` yöntemi veya başka bir Visual Basic kod.</span><span class="sxs-lookup"><span data-stu-id="77c5f-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="77c5f-110">Diğer programları tarafından tutulan nesne başvuruları geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="77c5f-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="77c5f-111">Varsa bir `End` deyimi içinde karşılaşıldığında bir `Try` veya `Catch` denetim bloğu değil geçirmek karşılık gelen `Finally` blok.</span><span class="sxs-lookup"><span data-stu-id="77c5f-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="77c5f-112">`Stop` Deyimi askıya alır, ancak yürütme `End`, tüm dosyaları kapatın veya desteklemez derlenmiş yürütülebilir (.exe) dosyasında karşılaşılanaa sürece herhangi bir değişkeni temizleyin.</span><span class="sxs-lookup"><span data-stu-id="77c5f-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="77c5f-113">Çünkü `End` uygulamanıza katılan sonlandırır açık olabilecek herhangi bir kaynakta, yakın düzgün bir şekilde kullanmadan önce aşağı denemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="77c5f-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="77c5f-114">Uygulamanızı açın herhangi bir form varsa, örneğin, bunları önce denetim ulaştığında kapatmalısınız `End` deyimi.</span><span class="sxs-lookup"><span data-stu-id="77c5f-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="77c5f-115">Kullanmanız gereken `End` tutumlu ve yalnızca gerektiğinde hemen durdurmak.</span><span class="sxs-lookup"><span data-stu-id="77c5f-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="77c5f-116">Bir yordam sonlandırmak için normal şekilde ([dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md) ve [çıkış bildirimi](../../../visual-basic/language-reference/statements/exit-statement.md)) yalnızca yordamı düzgün bir şekilde kapatın, ancak aynı zamanda çağıran kodun temiz kapatma aşağı fırsatı sunmak.</span><span class="sxs-lookup"><span data-stu-id="77c5f-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="77c5f-117">Örneğin, bir konsol uygulaması kolayca kaldırabilirsiniz `Return` gelen `Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="77c5f-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="77c5f-118">`End` Deyim aramaları <xref:System.Environment.Exit%2A> yöntemi <xref:System.Environment> sınıfını <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="77c5f-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="77c5f-119"><xref:System.Environment.Exit%2A> sahip olmasını gerektirir `UnmanagedCode` izni.</span><span class="sxs-lookup"><span data-stu-id="77c5f-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="77c5f-120">Değilse, bunu yaparsanız bir <xref:System.Security.SecurityException> hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="77c5f-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="77c5f-121">Ek bir anahtar tarafından izlendiğinde [son \<anahtar sözcüğü > deyimi](../../../visual-basic/language-reference/statements/end-keyword-statement.md) uygun yordamı ya da blok tanımının sonuna betimleyen.</span><span class="sxs-lookup"><span data-stu-id="77c5f-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="77c5f-122">Örneğin, `End Function` tanımını sonlandırır bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="77c5f-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77c5f-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="77c5f-123">Example</span></span>  
 <span data-ttu-id="77c5f-124">Aşağıdaki örnekte `End` kullanıcı isterse kod yürütmeyi sona erdirmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="77c5f-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="77c5f-125">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="77c5f-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="77c5f-126">Bu deyimi desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="77c5f-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77c5f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77c5f-127">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="77c5f-128">Stop Deyimi</span><span class="sxs-lookup"><span data-stu-id="77c5f-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)
- [<span data-ttu-id="77c5f-129">Son \<anahtar sözcüğü > deyimi</span><span class="sxs-lookup"><span data-stu-id="77c5f-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
