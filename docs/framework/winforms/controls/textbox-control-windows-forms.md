---
title: TextBox Denetimi (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text boxes
- TextBox control [Windows Forms]
ms.assetid: e5a06987-8aec-4271-b196-2245ba992d62
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d606140a5be2b1770bc5a16159e96e20b0fccdd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="textbox-control-windows-forms"></a><span data-ttu-id="c4131-102">TextBox Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c4131-102">TextBox Control (Windows Forms)</span></span>
<span data-ttu-id="c4131-103">Windows Forms metin kutuları kullanıcıdan giriş almak veya metni görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c4131-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="c4131-104">`TextBox` Salt okunur ayrıca çalışabilmesine rağmen denetim düzenlenebilir metin için genellikle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c4131-104">The `TextBox` control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="c4131-105">Metin kutuları birden çok satır görüntüleme, denetimin boyutunu metni kaydırma ve temel biçimlendirme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c4131-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="c4131-106">`TextBox` Görüntülenen veya denetimde girilen metin için tek bir biçim izin verir.</span><span class="sxs-lookup"><span data-stu-id="c4131-106">The `TextBox` control allows a single format for text displayed or entered in the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c4131-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c4131-107">In This Section</span></span>  
 [<span data-ttu-id="c4131-108">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c4131-108">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 <span data-ttu-id="c4131-109">Bu denetimi nedir ve anahtar özellikleri ve özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c4131-109">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="c4131-110">Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme</span><span class="sxs-lookup"><span data-stu-id="c4131-110">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 <span data-ttu-id="c4131-111">Ekleme noktasını düzenleme denetimi odağı ilk aldığında göründüğü belirtmek için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4131-111">Gives directions for specifying where the insertion point appears when an edit control first gets the focus.</span></span>  
  
 [<span data-ttu-id="c4131-112">Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4131-112">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="c4131-113">Bir metin kutusuna yazılan Gizle açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4131-113">Explains how to conceal what is typed into a text box.</span></span>  
  
 [<span data-ttu-id="c4131-114">Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4131-114">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 <span data-ttu-id="c4131-115">Bir metin kutusunun içeriğini değiştirilmesini engellemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="c4131-115">Describes how to prevent the contents of a text box from being changed.</span></span>  
  
 [<span data-ttu-id="c4131-116">Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma</span><span class="sxs-lookup"><span data-stu-id="c4131-116">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 <span data-ttu-id="c4131-117">Bir metin kutusu içindeki bir dizeye ekleme tırnak işaretleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4131-117">Explains adding quotation marks to a string in a text box.</span></span>  
  
 [<span data-ttu-id="c4131-118">Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme</span><span class="sxs-lookup"><span data-stu-id="c4131-118">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="c4131-119">Bir metin kutusundaki vurgulayın açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4131-119">Explains how to highlight text in a text box.</span></span>  
  
 [<span data-ttu-id="c4131-120">Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c4131-120">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="c4131-121">Bir metin kutusu kaydırılabilir nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4131-121">Describes how to make a text box scrollable.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c4131-122">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c4131-122">Reference</span></span>  
 <span data-ttu-id="c4131-123"><xref:System.Windows.Forms.TextBox>sınıfı</span><span class="sxs-lookup"><span data-stu-id="c4131-123"><xref:System.Windows.Forms.TextBox> class</span></span>  
 <span data-ttu-id="c4131-124">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="c4131-124">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c4131-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c4131-125">Related Sections</span></span>  
 [<span data-ttu-id="c4131-126">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="c4131-126">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="c4131-127">Windows Forms denetimleri, tam bir listesi ile bunların kullanılması hakkında bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4131-127">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
