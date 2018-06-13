---
title: Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- shortcuts [Windows Forms], controls
- keyboard shortcuts [Windows Forms], controls
- Windows Forms controls, labels
ms.assetid: 6eaf868c-819f-4131-8f59-048e20c286f7
ms.openlocfilehash: 0b75a4f59cdba4ff732a92996086b77bc65cf46c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535521"
---
# <a name="labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them"></a><span data-ttu-id="76260-102">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="76260-102">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>
<span data-ttu-id="76260-103">Windows Forms'a eklenen denetimler özelliklere sahip ve kullanıcı daha fazla özelleştirmek için kullanılan yöntemleri karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="76260-103">Controls added to Windows Forms have properties and methods that are used to further specialize the user experience.</span></span> <span data-ttu-id="76260-104">Kullanıcı gereksinimlerine uyacak şekilde, kullanıcı arabirimi özelleştirme, iyi tasarlanmış Windows uygulamaları için son derece önemlidir.</span><span class="sxs-lookup"><span data-stu-id="76260-104">Customizing your user interface to suit the needs of the user is extremely important for well-designed Windows applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="76260-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="76260-105">In This Section</span></span>  
 [<span data-ttu-id="76260-106">Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama</span><span class="sxs-lookup"><span data-stu-id="76260-106">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 <span data-ttu-id="76260-107">Bir metin etiketi denetime atama açıklar.</span><span class="sxs-lookup"><span data-stu-id="76260-107">Describes how to assign a text label to a control.</span></span>  
  
 [<span data-ttu-id="76260-108">Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Resmi Ayarlama</span><span class="sxs-lookup"><span data-stu-id="76260-108">How to: Set the Image Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)  
 <span data-ttu-id="76260-109">Görüntüleri göstermek için bir denetiminin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="76260-109">Explains how to configure a control to display images.</span></span>  
  
 [<span data-ttu-id="76260-110">Nasıl yapılır: Windows Forms Denetimleri için Erişim Tuşları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="76260-110">How to: Create Access Keys for Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 <span data-ttu-id="76260-111">Önceden tanımlanmış klavye kısayolları oluşturma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="76260-111">Gives information about creating predefined keyboard shortcuts.</span></span>  
  
 [<span data-ttu-id="76260-112">Bir Windows Formundaki Denetimler için Erişilebilirlik Bilgileri Sağlama</span><span class="sxs-lookup"><span data-stu-id="76260-112">Providing Accessibility Information for Controls on a Windows Form</span></span>](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md)  
 <span data-ttu-id="76260-113">Erişilebilirlik yardımları ile çalışmak denetimleri etkinleştirme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="76260-113">Gives information about enabling your controls to work with accessibility aids.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="76260-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="76260-114">Related Sections</span></span>  
 [<span data-ttu-id="76260-115">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="76260-115">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 <span data-ttu-id="76260-116">Diğer temel işlemleri için bağlantılar denetimleriyle yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76260-116">Links to other basic things you can do with controls.</span></span>  
  
 <span data-ttu-id="76260-117">Ayrıca bkz. [nasıl yapılır: oluşturmak erişim anahtarları için Windows Forms denetimleri kullanarak Tasarımcı](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [nasıl yapılır: Tasarımcı kullanarak bir Windows Forms denetimi görüntülenen metin ayarlamak](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [nasıl: resmi ayarlama Tarafından görüntülenen Tasarımcı kullanarak bir Windows Formları denetimi](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="76260-117">Also see [How to: Create Access Keys for Windows Forms Controls Using the Designer](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [How to: Set the Text Displayed by a Windows Forms Control Using the Designer](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [How to: Set the Image Displayed by a Windows Forms Control Using the Designer](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).</span></span>
