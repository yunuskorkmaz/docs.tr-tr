---
title: "Nasıl yapılır: Giriş Maskesini Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.MaskPropertyEditor
helpviewer_keywords: MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c136bd5bdacec04a011f728694550fb66ae6d897
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-set-the-input-mask"></a><span data-ttu-id="e3d7d-102">Nasıl yapılır: Giriş Maskesini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="e3d7d-102">How to: Set the Input Mask</span></span>
<span data-ttu-id="e3d7d-103">Maskelenmiş metin kutusu denetimi, kabul etme veya reddetme kullanıcı girişi için bir bildirim temelli söz dizimi destekleyen bir Gelişmiş metin kutusu denetimi ' dir.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-103">The masked text box control is an enhanced text box control that supports a declarative syntax for accepting or rejecting user input.</span></span> <span data-ttu-id="e3d7d-104">Mask özelliği ayarlayarak, uygulamanızda herhangi bir özel doğrulama mantık yazmadan izin verilen kullanıcı girişini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-104">By setting the Mask property, you can specify the allowable user input without writing any custom validation logic in your application.</span></span> <span data-ttu-id="e3d7d-105">Daha fazla bilgi için Açıklamalar bölümüne bakın <xref:System.Windows.Forms.MaskedTextBox> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-105">For more information, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox> class.</span></span>  
  
## <a name="setting-the-mask-property-manually"></a><span data-ttu-id="e3d7d-106">Mask özelliği el ile ayarlama</span><span class="sxs-lookup"><span data-stu-id="e3d7d-106">Setting the Mask Property Manually</span></span>  
 <span data-ttu-id="e3d7d-107">Maske özelliğini destekleyen karakterlerle hakkında bilginiz varsa, el ile girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-107">If you are familiar with the characters that the Mask property supports, you can enter it manually.</span></span> <span data-ttu-id="e3d7d-108">Maske özelliğini destekleyen karakterden oluşan bir özeti Açıklamalar bölümüne bakın <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-108">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
#### <a name="to-set-the-mask-property-manually"></a><span data-ttu-id="e3d7d-109">Mask özelliği el ile ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e3d7d-109">To set the Mask property manually</span></span>  
  
1.  <span data-ttu-id="e3d7d-110">İçinde **tasarım** görünümü, select bir <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-110">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
2.  <span data-ttu-id="e3d7d-111">İçinde **özellikleri** penceresinde bulun <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-111">In the **Properties** window, locate the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
3.  <span data-ttu-id="e3d7d-112">İstediğiniz maskesini yazın.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-112">Type the mask that you want.</span></span> <span data-ttu-id="e3d7d-113">Örneğin, `###`.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-113">For example, type `###`.</span></span>  
  
## <a name="using-the-input-mask-dialog-box"></a><span data-ttu-id="e3d7d-114">Giriş maskesi iletişim kutusunu kullanma</span><span class="sxs-lookup"><span data-stu-id="e3d7d-114">Using the Input Mask Dialog Box</span></span>  
 <span data-ttu-id="e3d7d-115">Giriş maskesi iletişim kutusu, bazı önceden tanımlanmış giriş maskeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-115">The Input Mask dialog box provides some predefined input masks.</span></span> <span data-ttu-id="e3d7d-116">Ayrıca, önceden tanımlanmış maskeleri değiştirebilir veya kendi maskesi el ile girin.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-116">You can also change the predefined masks or enter your own mask manually.</span></span>  
  
#### <a name="to-open-the-input-mask-dialog-box"></a><span data-ttu-id="e3d7d-117">Giriş maskesi iletişim kutusunu açmak için</span><span class="sxs-lookup"><span data-stu-id="e3d7d-117">To open the Input Mask dialog box</span></span>  
  
1.  <span data-ttu-id="e3d7d-118">İçinde **tasarım** görünümü, select bir <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-118">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
    1.  <span data-ttu-id="e3d7d-119">Akıllı etiket açmak için tıklatın **MaskedTextBox görevleri** paneli.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-119">Click the smart tag to open the **MaskedTextBox Tasks** panel.</span></span>  
  
    2.  <span data-ttu-id="e3d7d-120">Tıklatın **ayarlamak maskesi**.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-120">Click **Set Mask**.</span></span>  
  
     <span data-ttu-id="e3d7d-121">\-veya -</span><span class="sxs-lookup"><span data-stu-id="e3d7d-121">\- or -</span></span>  
  
    1.  <span data-ttu-id="e3d7d-122">İçinde **özellikleri** penceresinde, seçin <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-122">In the **Properties** window, select the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
    2.  <span data-ttu-id="e3d7d-123">Özellik değeri sütununda üç nokta düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-123">Click the ellipsis button in the property value column.</span></span>  
  
     <span data-ttu-id="e3d7d-124">**Giriş maskesi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-124">The **Input Mask** dialog box appears.</span></span>  
  
#### <a name="to-use-the-input-mask-dialog-box"></a><span data-ttu-id="e3d7d-125">Giriş maskesi iletişim kutusunu kullanma</span><span class="sxs-lookup"><span data-stu-id="e3d7d-125">To use the Input Mask dialog box</span></span>  
  
1.  <span data-ttu-id="e3d7d-126">(İsteğe bağlı) Önceden tanımlanmış maskeleri listesinde birini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-126">(Optional) Click one of the predefined masks in the list.</span></span>  
  
2.  <span data-ttu-id="e3d7d-127">(İsteğe bağlı) Önceden tanımlanmış maskesinde Düzenle **maskesi** kutusu.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-127">(Optional) Edit the predefined mask in the **Mask** box.</span></span>  
  
3.  <span data-ttu-id="e3d7d-128">(İsteğe bağlı) Yeni bir maskesi yazın **maskesi** kutusu.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-128">(Optional) Type a new mask in the **Mask** box.</span></span> <span data-ttu-id="e3d7d-129">Diğer bir deyişle, önceden tanımlanmış maskeleri birini kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-129">That is, you do not have to use one of the predefined masks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e3d7d-130">Önizleme kutusu içinde kullanıcı görür karakterleri görüntüler <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-130">The Preview box displays the characters that the user sees in the <xref:System.Windows.Forms.MaskedTextBox>.</span></span> <span data-ttu-id="e3d7d-131">Bu karakterler verileri doğru olarak girmiş kullanıcı yardımcı olacak bir kılavuz olur.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-131">These characters are a guide to help the user enter the data correctly.</span></span>  
  
4.  <span data-ttu-id="e3d7d-132">Seçin veya temizleyin **kullanım ValidatingType** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-132">Select or clear the **Use ValidatingType** check box.</span></span> <span data-ttu-id="e3d7d-133">**Kullanım ValidatingType** onay kutusu, bir veri türü veri girişi doğrulamak için kullanıcı tarafından kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-133">The **Use ValidatingType** check box specifies whether a data type is used to verify the data input by the user.</span></span> <span data-ttu-id="e3d7d-134">Daha fazla bilgi için bkz: <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-134">For more information, see the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property.</span></span>  
  
5.  <span data-ttu-id="e3d7d-135">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-135">Click **OK**.</span></span>  
  
     <span data-ttu-id="e3d7d-136">Maske girildiğini **maskesi** özelliğinde **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-136">The mask is entered in the **Mask** property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3d7d-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3d7d-137">See Also</span></span>  
 [<span data-ttu-id="e3d7d-138">İzlenecek yol: MaskedTextBox denetimiyle çalışma</span><span class="sxs-lookup"><span data-stu-id="e3d7d-138">Walkthrough: Working with the MaskedTextBox Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)
