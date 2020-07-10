---
title: TextBox Denetimi
description: Windows Forms TextBox denetiminin, düzenlenebilir metin için kullanılması ve salt okunurdur. gibi çeşitli yönleri hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes
- TextBox control [Windows Forms]
ms.assetid: e5a06987-8aec-4271-b196-2245ba992d62
ms.openlocfilehash: 026f6d2653e41dabd3db7490660b6ce19846d397
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174451"
---
# <a name="textbox-control-windows-forms"></a><span data-ttu-id="09ecb-103">TextBox Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="09ecb-103">TextBox Control (Windows Forms)</span></span>
<span data-ttu-id="09ecb-104">Windows Forms metin kutuları, kullanıcıdan giriş almak veya metin göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="09ecb-104">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="09ecb-105">`TextBox`Denetim genellikle düzenlenebilir metin için kullanılır, ancak salt okunabilir hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="09ecb-105">The `TextBox` control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="09ecb-106">Metin kutuları birden çok satır görüntüleyebilir, metni denetimin boyutuna kaydırabilirler ve temel biçimlendirme ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="09ecb-106">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="09ecb-107">`TextBox`Denetim, denetimde görünen veya girilen metin için tek bir biçime izin verir.</span><span class="sxs-lookup"><span data-stu-id="09ecb-107">The `TextBox` control allows a single format for text displayed or entered in the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="09ecb-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="09ecb-108">In This Section</span></span>  
 [<span data-ttu-id="09ecb-109">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="09ecb-109">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)  
 <span data-ttu-id="09ecb-110">Bu denetimin ne olduğunu ve temel özelliklerini ve özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="09ecb-110">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="09ecb-111">Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme</span><span class="sxs-lookup"><span data-stu-id="09ecb-111">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 <span data-ttu-id="09ecb-112">Bir düzenleme denetimi odağı ilk kez aldığında ekleme noktasının nerede göründüğünü belirtmek için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="09ecb-112">Gives directions for specifying where the insertion point appears when an edit control first gets the focus.</span></span>  
  
 [<span data-ttu-id="09ecb-113">Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="09ecb-113">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="09ecb-114">Metin kutusuna yazılan öğeleri nasıl gizlemek istediğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="09ecb-114">Explains how to conceal what is typed into a text box.</span></span>  
  
 [<span data-ttu-id="09ecb-115">Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="09ecb-115">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)  
 <span data-ttu-id="09ecb-116">Metin kutusu içeriğinin değiştirilmesini nasıl önleyebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="09ecb-116">Describes how to prevent the contents of a text box from being changed.</span></span>  
  
 [<span data-ttu-id="09ecb-117">Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma</span><span class="sxs-lookup"><span data-stu-id="09ecb-117">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 <span data-ttu-id="09ecb-118">Metin kutusundaki bir dizeye tırnak işareti eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="09ecb-118">Explains adding quotation marks to a string in a text box.</span></span>  
  
 [<span data-ttu-id="09ecb-119">Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme</span><span class="sxs-lookup"><span data-stu-id="09ecb-119">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="09ecb-120">Metin kutusunda metnin nasıl vurgulandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="09ecb-120">Explains how to highlight text in a text box.</span></span>  
  
 [<span data-ttu-id="09ecb-121">Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="09ecb-121">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="09ecb-122">Metin kutusunun kaydırılabilir hale getirme işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="09ecb-122">Describes how to make a text box scrollable.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="09ecb-123">Başvuru</span><span class="sxs-lookup"><span data-stu-id="09ecb-123">Reference</span></span>  
 <span data-ttu-id="09ecb-124"><xref:System.Windows.Forms.TextBox> sınıfı</span><span class="sxs-lookup"><span data-stu-id="09ecb-124"><xref:System.Windows.Forms.TextBox> class</span></span>  
 <span data-ttu-id="09ecb-125">Bu sınıfı açıklar ve tüm üyelerine bağlantıları vardır.</span><span class="sxs-lookup"><span data-stu-id="09ecb-125">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="09ecb-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="09ecb-126">Related Sections</span></span>  
 [<span data-ttu-id="09ecb-127">Windows Forms'ta Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="09ecb-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="09ecb-128">Windows Forms denetimlerinin tüm listesini, kullanımları hakkındaki bilgilerin bağlantılarıyla birlikte sağlar.</span><span class="sxs-lookup"><span data-stu-id="09ecb-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
