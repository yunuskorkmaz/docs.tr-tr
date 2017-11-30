---
title: "Nasıl yapılır: Değiştiricileri ve GenerateMember Özelliklerini Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
f1_keywords:
- Designer_GenerateMember
- Designer_Modifiers
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bcb79525e557a66ed471bc38dcbdd444d75ba6b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a><span data-ttu-id="e3fdc-102">Nasıl yapılır: Değiştiricileri ve GenerateMember Özelliklerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="e3fdc-102">How to: Use the Modifiers and GenerateMember Properties</span></span>
<span data-ttu-id="e3fdc-103">Bir Windows formunda bir bileşen yerleştirdiğinizde, iki özellik tasarım ortamı tarafından sağlanan: `GenerateMember` ve `Modifiers`.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-103">When you place a component on a Windows Form, two properties are provided by the design environment: `GenerateMember` and `Modifiers`.</span></span> <span data-ttu-id="e3fdc-104">`GenerateMember` Özelliği, Windows Form Tasarımcısı bileşeni için bir üye değişkenine oluşturduğunda belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-104">The `GenerateMember` property specifies when the Windows Forms Designer generates a member variable for a component.</span></span> <span data-ttu-id="e3fdc-105">`Modifiers` Bu üye değişkenine atanan erişim değiştiricisi bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-105">The `Modifiers` property is the access modifier assigned to that member variable.</span></span> <span data-ttu-id="e3fdc-106">Varsa değerini `GenerateMember` özelliği `false`, değeri `Modifiers` özelliğinin hiçbir etkisi.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-106">If the value of the `GenerateMember` property is `false`, the value of the `Modifiers` property has no effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3fdc-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e3fdc-108">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e3fdc-109">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="e3fdc-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-specify-whether-a-component-is-a-member-of-the-form"></a><span data-ttu-id="e3fdc-110">Bir bileşenin formun üyesi olup olmadığını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="e3fdc-110">To specify whether a component is a member of the form</span></span>  
  
1.  <span data-ttu-id="e3fdc-111">Windows Forms Tasarımcısı'nda formunuz açın.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-111">In the Windows Forms Designer, open your form.</span></span>  
  
2.  <span data-ttu-id="e3fdc-112">Açık **araç**ve form üzerinde üç yerleştirin <xref:System.Windows.Forms.Button> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-112">Open the **Toolbox**, and on the form, place three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
3.  <span data-ttu-id="e3fdc-113">Ayarlama `GenerateMember` ve `Modifiers` özellikleri her <xref:System.Windows.Forms.Button> denetimi aşağıdaki tabloya göre.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-113">Set the `GenerateMember` and `Modifiers` properties for each <xref:System.Windows.Forms.Button> control according to the following table.</span></span>  
  
    |<span data-ttu-id="e3fdc-114">Düğme adı</span><span class="sxs-lookup"><span data-stu-id="e3fdc-114">Button name</span></span>|<span data-ttu-id="e3fdc-115">GenerateMember değeri</span><span class="sxs-lookup"><span data-stu-id="e3fdc-115">GenerateMember value</span></span>|<span data-ttu-id="e3fdc-116">Değiştiriciler değeri</span><span class="sxs-lookup"><span data-stu-id="e3fdc-116">Modifiers value</span></span>|  
    |-----------------|--------------------------|---------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|<span data-ttu-id="e3fdc-117">Değişiklik yok</span><span class="sxs-lookup"><span data-stu-id="e3fdc-117">No change</span></span>|  
  
4.  <span data-ttu-id="e3fdc-118">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-118">Build the solution.</span></span>  
  
5.  <span data-ttu-id="e3fdc-119">İçinde **Çözüm Gezgini**, tıklatın **tüm dosyaları göster** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-119">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
6.  <span data-ttu-id="e3fdc-120">Açık **Form1** düğümünü ve **Kod Düzenleyicisi**açın **Form1.Designer.vb** veya **Form1.Designer.cs** dosya.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-120">Open the **Form1** node, and in the **Code Editor**,open the **Form1.Designer.vb** or **Form1.Designer.cs** file.</span></span> <span data-ttu-id="e3fdc-121">Bu dosyayı Windows Form Tasarımcısı tarafından gösterilen kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-121">This file contains the code emitted by the Windows Forms Designer.</span></span>  
  
7.  <span data-ttu-id="e3fdc-122">Üç düğme için bildirimleri bulun.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-122">Find the declarations for the three buttons.</span></span> <span data-ttu-id="e3fdc-123">Aşağıdaki kod örneği tarafından belirtilen farklar gösterilmektedir `GenerateMember` ve `Modifiers` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-123">The following code example shows the differences specified by the `GenerateMember` and `Modifiers` properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  <span data-ttu-id="e3fdc-124">Varsayılan olarak, Windows Form Tasarımcısı atar `private` (`Friend` Visual Basic'te) kapsayıcı denetimleri gibi değiştiriciyi <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-124">By default, the Windows Forms Designer assigns the `private` (`Friend` in Visual Basic) modifier to container controls like <xref:System.Windows.Forms.Panel>.</span></span> <span data-ttu-id="e3fdc-125">Varsa tabanınızı <xref:System.Windows.Forms.UserControl> veya <xref:System.Windows.Forms.Form> bir kapsayıcı denetiminin devralınan denetimleri ve formlar yeni alt kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-125">If your base <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Form> has a container control, it will not accept new children in inherited controls and forms.</span></span> <span data-ttu-id="e3fdc-126">Çözüm için temel kapsayıcı denetiminin değiştiricisi değiştirmektir `protected` veya `public`.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-126">The solution is to change the modifier of the base container control to `protected` or `public`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3fdc-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3fdc-127">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="e3fdc-128">Windows Forms görsel devralma</span><span class="sxs-lookup"><span data-stu-id="e3fdc-128">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [<span data-ttu-id="e3fdc-129">İzlenecek yol: Görsel devralmayı gösterme</span><span class="sxs-lookup"><span data-stu-id="e3fdc-129">Walkthrough: Demonstrating Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 [<span data-ttu-id="e3fdc-130">Nasıl yapılır: Windows formlarını devralma</span><span class="sxs-lookup"><span data-stu-id="e3fdc-130">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)
