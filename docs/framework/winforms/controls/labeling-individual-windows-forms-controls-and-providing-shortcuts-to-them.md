---
title: Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- shortcuts [Windows Forms], controls
- keyboard shortcuts [Windows Forms], controls
- Windows Forms controls, labels
ms.assetid: 6eaf868c-819f-4131-8f59-048e20c286f7
ms.openlocfilehash: a5504095814cdfc04699bf24b9b96191e94b22c3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43409026"
---
# <a name="labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them"></a><span data-ttu-id="1ee0d-102">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="1ee0d-102">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>
<span data-ttu-id="1ee0d-103">Windows Forms için eklenen denetimler özelliklere sahip ve daha fazla kullanıcı özelleştirmek üzere kullanılan yöntemleri karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="1ee0d-103">Controls added to Windows Forms have properties and methods that are used to further specialize the user experience.</span></span> <span data-ttu-id="1ee0d-104">Kullanıcı gereksinimlerine uyacak şekilde, kullanıcı arabirimini özelleştirme, iyi tasarlanmış Windows uygulamaları için son derece önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1ee0d-104">Customizing your user interface to suit the needs of the user is extremely important for well-designed Windows applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ee0d-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1ee0d-105">In This Section</span></span>  
 [<span data-ttu-id="1ee0d-106">Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama</span><span class="sxs-lookup"><span data-stu-id="1ee0d-106">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 <span data-ttu-id="1ee0d-107">Bir denetime metin etiketi atamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="1ee0d-107">Describes how to assign a text label to a control.</span></span>  
  
 [<span data-ttu-id="1ee0d-108">Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Resmi Ayarlama</span><span class="sxs-lookup"><span data-stu-id="1ee0d-108">How to: Set the Image Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)  
 <span data-ttu-id="1ee0d-109">Resimleri görüntülemek için bir denetimi yapılandırma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1ee0d-109">Explains how to configure a control to display images.</span></span>  
  
 [<span data-ttu-id="1ee0d-110">Nasıl yapılır: Windows Forms Denetimleri için Erişim Tuşları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1ee0d-110">How to: Create Access Keys for Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 <span data-ttu-id="1ee0d-111">Önceden tanımlı klavye kısayolları oluşturma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ee0d-111">Gives information about creating predefined keyboard shortcuts.</span></span>  
  
 [<span data-ttu-id="1ee0d-112">Bir Windows Formundaki Denetimler için Erişilebilirlik Bilgileri Sağlama</span><span class="sxs-lookup"><span data-stu-id="1ee0d-112">Providing Accessibility Information for Controls on a Windows Form</span></span>](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md)  
 <span data-ttu-id="1ee0d-113">Denetimlerinizi erişilebilirlik Yardımcıları ile çalışacak şekilde etkinleştirme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ee0d-113">Gives information about enabling your controls to work with accessibility aids.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1ee0d-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="1ee0d-114">Related Sections</span></span>  
 [<span data-ttu-id="1ee0d-115">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="1ee0d-115">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 <span data-ttu-id="1ee0d-116">Temel başka şeyler için bağlantı denetimleri ile yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ee0d-116">Links to other basic things you can do with controls.</span></span>  
  
 <span data-ttu-id="1ee0d-117">Ayrıca bkz: [nasıl yapılır: erişim anahtarları için Windows Forms denetimleri kullanarak Tasarımcı](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md), [nasıl yapılır: Tasarımcı bir Windows Forms denetimini kullanarak tarafından görüntülenen metni ayarlama](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md), [nasıl yapılır: resmi ayarlama Tarafından görüntülenen bir Windows Forms Tasarımcısı'nı kullanarak denetimi](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="1ee0d-117">Also see [How to: Create Access Keys for Windows Forms Controls Using the Designer](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md), [How to: Set the Text Displayed by a Windows Forms Control Using the Designer](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md), [How to: Set the Image Displayed by a Windows Forms Control Using the Designer](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md).</span></span>
