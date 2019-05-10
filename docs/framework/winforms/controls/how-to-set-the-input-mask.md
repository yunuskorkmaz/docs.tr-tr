---
title: 'Nasıl yapılır: Giriş Maskesini Ayarlama'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: dd156f9e5bf6519363f66ca61687f1e9f2bfc6ab
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630423"
---
# <a name="how-to-set-the-input-mask"></a><span data-ttu-id="a63fb-102">Nasıl yapılır: Giriş Maskesini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="a63fb-102">How to: Set the Input Mask</span></span>
<span data-ttu-id="a63fb-103">Maskelenmiş metin kutusu denetimini kabul etme veya reddetme kullanıcı girişi için bir bildirim temelli söz dizimi destekleyen Gelişmiş metin kutusu denetimidir.</span><span class="sxs-lookup"><span data-stu-id="a63fb-103">The masked text box control is an enhanced text box control that supports a declarative syntax for accepting or rejecting user input.</span></span> <span data-ttu-id="a63fb-104">Maske özelliği ayarlayarak, uygulamanızda herhangi bir özel doğrulama mantığı yazmak zorunda kalmadan izin verilen kullanıcı girişini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a63fb-104">By setting the Mask property, you can specify the allowable user input without writing any custom validation logic in your application.</span></span> <span data-ttu-id="a63fb-105">Daha fazla bilgi için Açıklamalar bölümüne bakın. <xref:System.Windows.Forms.MaskedTextBox> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a63fb-105">For more information, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox> class.</span></span>  
  
## <a name="setting-the-mask-property-manually"></a><span data-ttu-id="a63fb-106">Maske özelliği el ile ayarlama</span><span class="sxs-lookup"><span data-stu-id="a63fb-106">Setting the Mask Property Manually</span></span>  
 <span data-ttu-id="a63fb-107">Maske özelliği destekleyen karakterlerle biliyorsanız, el ile girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a63fb-107">If you are familiar with the characters that the Mask property supports, you can enter it manually.</span></span> <span data-ttu-id="a63fb-108">Maske özelliği destekleyen karakterleri özeti için Açıklamalar bölümüne bakın. <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a63fb-108">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
#### <a name="to-set-the-mask-property-manually"></a><span data-ttu-id="a63fb-109">Maske özelliği el ile ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a63fb-109">To set the Mask property manually</span></span>  
  
1. <span data-ttu-id="a63fb-110">İçinde **tasarım** görüntülenecek bir <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="a63fb-110">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
2. <span data-ttu-id="a63fb-111">İçinde **özellikleri** penceresinde bulun <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a63fb-111">In the **Properties** window, locate the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
3. <span data-ttu-id="a63fb-112">İstediğiniz maske yazın.</span><span class="sxs-lookup"><span data-stu-id="a63fb-112">Type the mask that you want.</span></span> <span data-ttu-id="a63fb-113">Örneğin, `###`.</span><span class="sxs-lookup"><span data-stu-id="a63fb-113">For example, type `###`.</span></span>  
  
## <a name="using-the-input-mask-dialog-box"></a><span data-ttu-id="a63fb-114">Giriş maskesi iletişim kutusunu kullanma</span><span class="sxs-lookup"><span data-stu-id="a63fb-114">Using the Input Mask Dialog Box</span></span>  
 <span data-ttu-id="a63fb-115">Giriş maskesi iletişim kutusu, bazı önceden tanımlanmış giriş maskeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a63fb-115">The Input Mask dialog box provides some predefined input masks.</span></span> <span data-ttu-id="a63fb-116">Ayrıca, önceden tanımlanmış maskeleri değiştirebilir veya kendi maskesini el ile girin.</span><span class="sxs-lookup"><span data-stu-id="a63fb-116">You can also change the predefined masks or enter your own mask manually.</span></span>  
  
#### <a name="to-open-the-input-mask-dialog-box"></a><span data-ttu-id="a63fb-117">Giriş maskesi iletişim kutusunu açmak için</span><span class="sxs-lookup"><span data-stu-id="a63fb-117">To open the Input Mask dialog box</span></span>  
  
1. <span data-ttu-id="a63fb-118">İçinde **tasarım** görüntülenecek bir <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="a63fb-118">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
    1. <span data-ttu-id="a63fb-119">Akıllı etiket açmak için tıklayın **MaskedTextBox görevleri** paneli.</span><span class="sxs-lookup"><span data-stu-id="a63fb-119">Click the smart tag to open the **MaskedTextBox Tasks** panel.</span></span>  
  
    2. <span data-ttu-id="a63fb-120">Tıklayın **ayarlamak maskesi**.</span><span class="sxs-lookup"><span data-stu-id="a63fb-120">Click **Set Mask**.</span></span>  
  
     <span data-ttu-id="a63fb-121">\- veya -</span><span class="sxs-lookup"><span data-stu-id="a63fb-121">\- or -</span></span>  
  
    1. <span data-ttu-id="a63fb-122">İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a63fb-122">In the **Properties** window, select the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
    2. <span data-ttu-id="a63fb-123">Özellik değer sütununa üç nokta düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a63fb-123">Click the ellipsis button in the property value column.</span></span>  
  
     <span data-ttu-id="a63fb-124">**Giriş maskesi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a63fb-124">The **Input Mask** dialog box appears.</span></span>  
  
#### <a name="to-use-the-input-mask-dialog-box"></a><span data-ttu-id="a63fb-125">Giriş maskesi iletişim kutusunu kullanma</span><span class="sxs-lookup"><span data-stu-id="a63fb-125">To use the Input Mask dialog box</span></span>  
  
1. <span data-ttu-id="a63fb-126">(İsteğe bağlı) Önceden tanımlanmış maskeleri listesinde birine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a63fb-126">(Optional) Click one of the predefined masks in the list.</span></span>  
  
2. <span data-ttu-id="a63fb-127">(İsteğe bağlı) Önceden tanımlanmış maskesinde Düzenle **maskesi** kutusu.</span><span class="sxs-lookup"><span data-stu-id="a63fb-127">(Optional) Edit the predefined mask in the **Mask** box.</span></span>  
  
3. <span data-ttu-id="a63fb-128">(İsteğe bağlı) Yeni bir maskesi yazın **maskesi** kutusu.</span><span class="sxs-lookup"><span data-stu-id="a63fb-128">(Optional) Type a new mask in the **Mask** box.</span></span> <span data-ttu-id="a63fb-129">Diğer bir deyişle, önceden tanımlanmış maskeleri birini kullanın gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a63fb-129">That is, you do not have to use one of the predefined masks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a63fb-130">Önizleme kutusunu görüntüler, kullanıcının gördüğü karakterleri <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="a63fb-130">The Preview box displays the characters that the user sees in the <xref:System.Windows.Forms.MaskedTextBox>.</span></span> <span data-ttu-id="a63fb-131">Bu verileri doğru olarak girmiş kullanıcı yardımcı olacak bir kılavuz karakterleridir.</span><span class="sxs-lookup"><span data-stu-id="a63fb-131">These characters are a guide to help the user enter the data correctly.</span></span>  
  
4. <span data-ttu-id="a63fb-132">Seçin veya temizleyin **kullanım ValidatingType** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="a63fb-132">Select or clear the **Use ValidatingType** check box.</span></span> <span data-ttu-id="a63fb-133">**Kullanım ValidatingType** onay kutusu, bir veri türü veri girişi doğrulamak için kullanıcı tarafından kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a63fb-133">The **Use ValidatingType** check box specifies whether a data type is used to verify the data input by the user.</span></span> <span data-ttu-id="a63fb-134">Daha fazla bilgi için <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a63fb-134">For more information, see the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property.</span></span>  
  
5. <span data-ttu-id="a63fb-135">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a63fb-135">Click **OK**.</span></span>  
  
     <span data-ttu-id="a63fb-136">Maske girildiğini **maskesi** özelliğinde **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="a63fb-136">The mask is entered in the **Mask** property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a63fb-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a63fb-137">See also</span></span>

- [<span data-ttu-id="a63fb-138">İzlenecek yol: MaskedTextBox denetimiyle çalışma</span><span class="sxs-lookup"><span data-stu-id="a63fb-138">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
