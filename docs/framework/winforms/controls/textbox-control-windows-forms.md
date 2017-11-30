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
ms.openlocfilehash: 4800b06b5d0bbc5ce51d7cf00798ca98ef8bf656
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="textbox-control-windows-forms"></a><span data-ttu-id="6b500-102">TextBox Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6b500-102">TextBox Control (Windows Forms)</span></span>
<span data-ttu-id="6b500-103">Windows Forms metin kutuları kullanıcıdan giriş almak veya metni görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b500-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="6b500-104">`TextBox` Salt okunur ayrıca çalışabilmesine rağmen denetim düzenlenebilir metin için genellikle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b500-104">The `TextBox` control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="6b500-105">Metin kutuları birden çok satır görüntüleme, denetimin boyutunu metni kaydırma ve temel biçimlendirme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6b500-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="6b500-106">`TextBox` Görüntülenen veya denetimde girilen metin için tek bir biçim izin verir.</span><span class="sxs-lookup"><span data-stu-id="6b500-106">The `TextBox` control allows a single format for text displayed or entered in the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b500-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6b500-107">In This Section</span></span>  
 [<span data-ttu-id="6b500-108">TextBox denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="6b500-108">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 <span data-ttu-id="6b500-109">Bu denetimi nedir ve anahtar özellikleri ve özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6b500-109">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="6b500-110">Nasıl yapılır: Windows Forms TextBox denetiminde ekleme noktasını denetleme</span><span class="sxs-lookup"><span data-stu-id="6b500-110">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 <span data-ttu-id="6b500-111">Ekleme noktasını düzenleme denetimi odağı ilk aldığında göründüğü belirtmek için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b500-111">Gives directions for specifying where the insertion point appears when an edit control first gets the focus.</span></span>  
  
 [<span data-ttu-id="6b500-112">Nasıl yapılır: Windows Forms TextBox denetimi ile parola metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="6b500-112">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="6b500-113">Bir metin kutusuna yazılan Gizle açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b500-113">Explains how to conceal what is typed into a text box.</span></span>  
  
 [<span data-ttu-id="6b500-114">Nasıl yapılır: salt okunur metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="6b500-114">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 <span data-ttu-id="6b500-115">Bir metin kutusunun içeriğini değiştirilmesini engellemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="6b500-115">Describes how to prevent the contents of a text box from being changed.</span></span>  
  
 [<span data-ttu-id="6b500-116">Nasıl yapılır: dizeye tırnak işaretleri koyma</span><span class="sxs-lookup"><span data-stu-id="6b500-116">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 <span data-ttu-id="6b500-117">Bir metin kutusu içindeki bir dizeye ekleme tırnak işaretleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b500-117">Explains adding quotation marks to a string in a text box.</span></span>  
  
 [<span data-ttu-id="6b500-118">Nasıl yapılır: metni seçme Windows Forms TextBox denetiminde</span><span class="sxs-lookup"><span data-stu-id="6b500-118">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="6b500-119">Bir metin kutusundaki vurgulayın açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b500-119">Explains how to highlight text in a text box.</span></span>  
  
 [<span data-ttu-id="6b500-120">Nasıl yapılır: birden çok satır Windows Forms TextBox denetiminde görünümü</span><span class="sxs-lookup"><span data-stu-id="6b500-120">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="6b500-121">Bir metin kutusu kaydırılabilir nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b500-121">Describes how to make a text box scrollable.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6b500-122">Başvuru</span><span class="sxs-lookup"><span data-stu-id="6b500-122">Reference</span></span>  
 <span data-ttu-id="6b500-123"><xref:System.Windows.Forms.TextBox>sınıfı</span><span class="sxs-lookup"><span data-stu-id="6b500-123"><xref:System.Windows.Forms.TextBox> class</span></span>  
 <span data-ttu-id="6b500-124">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="6b500-124">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6b500-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6b500-125">Related Sections</span></span>  
 [<span data-ttu-id="6b500-126">Windows Forms'ta kullanılacak denetimler</span><span class="sxs-lookup"><span data-stu-id="6b500-126">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="6b500-127">Windows Forms denetimleri, tam bir listesi ile bunların kullanılması hakkında bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b500-127">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
