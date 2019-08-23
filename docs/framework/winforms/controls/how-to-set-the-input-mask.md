---
title: 'Nasıl yapılır: Giriş Maskesini Ayarlama'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 06dee48765653ac7a659246cc3dfe865c795ca21
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949142"
---
# <a name="how-to-set-the-input-mask"></a><span data-ttu-id="0fe88-102">Nasıl yapılır: Giriş Maskesini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="0fe88-102">How to: Set the Input Mask</span></span>
<span data-ttu-id="0fe88-103">Maskelenmiş metin kutusu denetimi, Kullanıcı girişini kabul etmek veya reddetmek için bildirime dayalı bir sözdizimi destekleyen, Gelişmiş metin kutusu denetimidir.</span><span class="sxs-lookup"><span data-stu-id="0fe88-103">The masked text box control is an enhanced text box control that supports a declarative syntax for accepting or rejecting user input.</span></span> <span data-ttu-id="0fe88-104">Maske özelliğini ayarlayarak, uygulamanızda herhangi bir özel doğrulama mantığı yazmadan izin verilen kullanıcı girişini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fe88-104">By setting the Mask property, you can specify the allowable user input without writing any custom validation logic in your application.</span></span> <span data-ttu-id="0fe88-105">Daha fazla bilgi için, <xref:System.Windows.Forms.MaskedTextBox> sınıfının açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0fe88-105">For more information, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox> class.</span></span>  
  
## <a name="setting-the-mask-property-manually"></a><span data-ttu-id="0fe88-106">Maske özelliğini el Ile ayarlama</span><span class="sxs-lookup"><span data-stu-id="0fe88-106">Setting the Mask Property Manually</span></span>  
 <span data-ttu-id="0fe88-107">Maske özelliğinin desteklediği karakterleri biliyorsanız, el ile girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fe88-107">If you are familiar with the characters that the Mask property supports, you can enter it manually.</span></span> <span data-ttu-id="0fe88-108">Maske özelliğinin desteklediği karakterlerin bir özeti için, <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliğinin açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0fe88-108">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
### <a name="to-set-the-mask-property-manually"></a><span data-ttu-id="0fe88-109">Maske özelliğini el ile ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="0fe88-109">To set the Mask property manually</span></span>  
  
1. <span data-ttu-id="0fe88-110">**Tasarım** görünümü ' nde bir <xref:System.Windows.Forms.MaskedTextBox>seçin.</span><span class="sxs-lookup"><span data-stu-id="0fe88-110">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
2. <span data-ttu-id="0fe88-111">**Özellikler** penceresinde, <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliğini bulun.</span><span class="sxs-lookup"><span data-stu-id="0fe88-111">In the **Properties** window, locate the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
3. <span data-ttu-id="0fe88-112">İstediğiniz maskeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="0fe88-112">Type the mask that you want.</span></span> <span data-ttu-id="0fe88-113">Örneğin `###`yazın.</span><span class="sxs-lookup"><span data-stu-id="0fe88-113">For example, type `###`.</span></span>  
  
## <a name="using-the-input-mask-dialog-box"></a><span data-ttu-id="0fe88-114">Giriş maskesi Iletişim kutusunu kullanma</span><span class="sxs-lookup"><span data-stu-id="0fe88-114">Using the Input Mask Dialog Box</span></span>  
 <span data-ttu-id="0fe88-115">Giriş maskesi iletişim kutusu bazı önceden tanımlanmış giriş maskeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fe88-115">The Input Mask dialog box provides some predefined input masks.</span></span> <span data-ttu-id="0fe88-116">Ayrıca, önceden tanımlanmış maskeleri değiştirebilir veya kendi maskesini el ile girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fe88-116">You can also change the predefined masks or enter your own mask manually.</span></span>  
  
### <a name="to-open-the-input-mask-dialog-box"></a><span data-ttu-id="0fe88-117">Giriş maskesi iletişim kutusunu açmak için</span><span class="sxs-lookup"><span data-stu-id="0fe88-117">To open the Input Mask dialog box</span></span>  
  
1. <span data-ttu-id="0fe88-118">**Tasarım** görünümü ' nde bir <xref:System.Windows.Forms.MaskedTextBox>seçin.</span><span class="sxs-lookup"><span data-stu-id="0fe88-118">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
    1. <span data-ttu-id="0fe88-119">Akıllı etikete tıklayarak **MaskedTextBox görevler** panelini açın.</span><span class="sxs-lookup"><span data-stu-id="0fe88-119">Click the smart tag to open the **MaskedTextBox Tasks** panel.</span></span>  
  
    2. <span data-ttu-id="0fe88-120">**Maskeyi ayarla**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0fe88-120">Click **Set Mask**.</span></span>  
  
     <span data-ttu-id="0fe88-121">\- veya -</span><span class="sxs-lookup"><span data-stu-id="0fe88-121">\- or -</span></span>  
  
    1. <span data-ttu-id="0fe88-122">**Özellikler** penceresinde, <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği seçin.</span><span class="sxs-lookup"><span data-stu-id="0fe88-122">In the **Properties** window, select the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
    2. <span data-ttu-id="0fe88-123">Özellik değeri sütunundaki üç nokta düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0fe88-123">Click the ellipsis button in the property value column.</span></span>  
  
     <span data-ttu-id="0fe88-124">**Giriş maskesi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0fe88-124">The **Input Mask** dialog box appears.</span></span>  
  
### <a name="to-use-the-input-mask-dialog-box"></a><span data-ttu-id="0fe88-125">Giriş maskesi iletişim kutusunu kullanmak için</span><span class="sxs-lookup"><span data-stu-id="0fe88-125">To use the Input Mask dialog box</span></span>  
  
1. <span data-ttu-id="0fe88-126">Seçim Listede önceden tanımlanmış maskelerden birine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0fe88-126">(Optional) Click one of the predefined masks in the list.</span></span>  
  
2. <span data-ttu-id="0fe88-127">Seçim **Maske** kutusunda önceden tanımlanmış maskeyi düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="0fe88-127">(Optional) Edit the predefined mask in the **Mask** box.</span></span>  
  
3. <span data-ttu-id="0fe88-128">Seçim **Maske** kutusuna yeni bir maske yazın.</span><span class="sxs-lookup"><span data-stu-id="0fe88-128">(Optional) Type a new mask in the **Mask** box.</span></span> <span data-ttu-id="0fe88-129">Diğer bir deyişle, önceden tanımlanmış maskelerden birini kullanmak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fe88-129">That is, you do not have to use one of the predefined masks.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0fe88-130">Önizleme kutusunda kullanıcının içinde <xref:System.Windows.Forms.MaskedTextBox>gördüğü karakterler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0fe88-130">The Preview box displays the characters that the user sees in the <xref:System.Windows.Forms.MaskedTextBox>.</span></span> <span data-ttu-id="0fe88-131">Bu karakterler, kullanıcının verileri doğru şekilde girmesine yardımcı olan kılavuzlardır.</span><span class="sxs-lookup"><span data-stu-id="0fe88-131">These characters are a guide to help the user enter the data correctly.</span></span>  
  
4. <span data-ttu-id="0fe88-132">**ValidatingType kullan** onay kutusunu seçin veya temizleyin.</span><span class="sxs-lookup"><span data-stu-id="0fe88-132">Select or clear the **Use ValidatingType** check box.</span></span> <span data-ttu-id="0fe88-133">**Use ValidatingType** onay kutusu, Kullanıcı tarafından veri girişini doğrulamak için bir veri türünün kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0fe88-133">The **Use ValidatingType** check box specifies whether a data type is used to verify the data input by the user.</span></span> <span data-ttu-id="0fe88-134">Daha fazla bilgi için bkz <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> . özelliği.</span><span class="sxs-lookup"><span data-stu-id="0fe88-134">For more information, see the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property.</span></span>  
  
5. <span data-ttu-id="0fe88-135">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="0fe88-135">Click **OK**.</span></span>  
  
     <span data-ttu-id="0fe88-136">Maske, **Özellikler** penceresindeki **maske** özelliğinde girilir.</span><span class="sxs-lookup"><span data-stu-id="0fe88-136">The mask is entered in the **Mask** property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fe88-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fe88-137">See also</span></span>

- [<span data-ttu-id="0fe88-138">İzlenecek yol: MaskedTextBox denetimiyle çalışma</span><span class="sxs-lookup"><span data-stu-id="0fe88-138">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
