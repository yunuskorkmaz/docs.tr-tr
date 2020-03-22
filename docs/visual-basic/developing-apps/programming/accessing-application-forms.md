---
title: Uygulama Formlarına Erişme
ms.date: 07/20/2015
helpviewer_keywords:
- forms [Visual Basic], communicating between
- application forms [Visual Basic], accessing
- forms [Visual Basic], accessing one from another
- My.Forms object
- forms [Visual Basic], accessing all open
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
ms.openlocfilehash: 332b6a7563160528b6c17210170af0db6e9bc0e7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349235"
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="d7326-102">Uygulama Formlarına Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7326-102">Accessing Application Forms (Visual Basic)</span></span>

<span data-ttu-id="d7326-103">Nesne, `My.Forms` uygulamanın projesinde bildirilen her Windows Formu örneğine erişmek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7326-103">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="d7326-104">Ayrıca, uygulamanın sıçrama `My.Application` ekranına ve ana formuna erişmek ve uygulamanın açık formlarının bir listesini almak için nesnenin özelliklerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7326-104">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="d7326-105">Görevler</span><span class="sxs-lookup"><span data-stu-id="d7326-105">Tasks</span></span>  

 <span data-ttu-id="d7326-106">Aşağıdaki tabloda, bir uygulamanın formlarına nasıl erişilenleri gösteren örnekler listeleilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d7326-106">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="d7326-107">Alıcı</span><span class="sxs-lookup"><span data-stu-id="d7326-107">To</span></span>|<span data-ttu-id="d7326-108">Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7326-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="d7326-109">Bir uygulamada bir formdan başka bir formdan erişin.</span><span class="sxs-lookup"><span data-stu-id="d7326-109">Access one form from another form in an application.</span></span>|[<span data-ttu-id="d7326-110">My.Forms Nesnesi</span><span class="sxs-lookup"><span data-stu-id="d7326-110">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="d7326-111">Tüm uygulamanın açık formlarının başlıklarını görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="d7326-111">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="d7326-112">Uygulama başlarken sıçrama ekranını durum bilgileriyle güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="d7326-112">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="d7326-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7326-113">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>
- [<span data-ttu-id="d7326-114">My.Forms Nesnesi</span><span class="sxs-lookup"><span data-stu-id="d7326-114">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
