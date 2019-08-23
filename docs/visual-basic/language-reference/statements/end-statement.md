---
title: End ekstresi (Visual Basic)
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
ms.openlocfilehash: 9307cf10e6125441bd49baa0e663a5a13f234005
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944460"
---
# <a name="end-statement"></a><span data-ttu-id="195e7-102">End Deyimi</span><span class="sxs-lookup"><span data-stu-id="195e7-102">End Statement</span></span>
<span data-ttu-id="195e7-103">Yürütmeyi hemen sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="195e7-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="195e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="195e7-104">Syntax</span></span>  
  
```  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="195e7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="195e7-105">Remarks</span></span>  
 <span data-ttu-id="195e7-106">Tüm uygulamayı çalışmayı durdurmayı `End` zorlamak için ifadeyi bir yordamda herhangi bir yere yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="195e7-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="195e7-107">`End``Open` ifadesiyle açılan tüm dosyaları kapatır ve tüm uygulamanın değişkenlerini temizler.</span><span class="sxs-lookup"><span data-stu-id="195e7-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="195e7-108">Nesneleri, nesnelerine başvuruları tutan başka hiçbir program yoksa ve kodun hiçbiri çalışmıyorsa, uygulama kapanır.</span><span class="sxs-lookup"><span data-stu-id="195e7-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="195e7-109">İfade kod yürütmeyi aniden durduruyor ve `Dispose` ya `Finalize` da metodunu ya da başka bir Visual Basic kodunu çağırmaz. `End`</span><span class="sxs-lookup"><span data-stu-id="195e7-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="195e7-110">Diğer programlar tarafından tutulan nesne başvuruları geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="195e7-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="195e7-111">Bir `End` `Finally` veya bloğu`Catch` içinde bir ifadeye karşılaşılırsa, denetim karşılık gelen bloğa geçmez. `Try`</span><span class="sxs-lookup"><span data-stu-id="195e7-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="195e7-112">İfade yürütmeyi askıya alır, ancak farklı `End`olarak, derlenmiş bir çalıştırılabilir (. exe) dosyasında karşılaşılmadığı takdirde herhangi bir dosyayı kapatmaz veya hiçbir değişkeni temizlemez. `Stop`</span><span class="sxs-lookup"><span data-stu-id="195e7-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="195e7-113">Açık `End` olabilecek kaynaklara katılmadan uygulamanızı sonlandırdığından, kullanmadan önce düzgün bir şekilde kapatmayı denemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="195e7-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="195e7-114">Örneğin, uygulamanızda açık bir form varsa, Denetim `End` ifadeye ulaşmadan önce bunları kapatmalısınız.</span><span class="sxs-lookup"><span data-stu-id="195e7-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="195e7-115">Gelişigüzel ve yalnızca `End` hemen durdurmanız gerektiğinde kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="195e7-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="195e7-116">Bir yordamı ([Return deyimleri](../../../visual-basic/language-reference/statements/return-statement.md) ve [Exit ifadesini](../../../visual-basic/language-reference/statements/exit-statement.md)) sonlandırmak için normal yollar, yordamı yalnızca düzgün bir şekilde kapatmaz, aynı zamanda çağıran koda düzgün bir şekilde kapatma fırsatı verir.</span><span class="sxs-lookup"><span data-stu-id="195e7-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="195e7-117">Örneğin, bir konsol uygulaması yalnızca `Return` `Main` yordamdan olabilir.</span><span class="sxs-lookup"><span data-stu-id="195e7-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="195e7-118">İfade, <xref:System.Environment.Exit%2A> <xref:System.Environment> ad alanındaki sınıfının yöntemini çağırır. <xref:System> `End`</span><span class="sxs-lookup"><span data-stu-id="195e7-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="195e7-119"><xref:System.Environment.Exit%2A>izninizin olması `UnmanagedCode` gerekir.</span><span class="sxs-lookup"><span data-stu-id="195e7-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="195e7-120">Aksi takdirde bir <xref:System.Security.SecurityException> hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="195e7-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="195e7-121">Sonrasında ek bir anahtar sözcük, [End \<anahtar sözcüğü > deyimin](../../../visual-basic/language-reference/statements/end-keyword-statement.md) uygun yordam veya bloğun tanımının sonuna göre ayırıcıları.</span><span class="sxs-lookup"><span data-stu-id="195e7-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="195e7-122">Örneğin, `End Function` bir `Function` yordamın tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="195e7-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="195e7-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="195e7-123">Example</span></span>  
 <span data-ttu-id="195e7-124">Aşağıdaki örnek, Kullanıcı istediğinde `End` kod yürütmeyi sonlandırmak için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="195e7-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="195e7-125">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="195e7-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="195e7-126">Bu ifade desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="195e7-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="195e7-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="195e7-127">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="195e7-128">Stop Deyimi</span><span class="sxs-lookup"><span data-stu-id="195e7-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)
- [<span data-ttu-id="195e7-129">End \<anahtar sözcüğü > ekstresi</span><span class="sxs-lookup"><span data-stu-id="195e7-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
