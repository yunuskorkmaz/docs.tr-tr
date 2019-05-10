---
title: 'Nasıl yapılır: Değiştiricileri ve GenerateMember Özelliklerini Kullanma'
ms.date: 03/30/2017
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
ms.openlocfilehash: 3fbaaae53aa60f6356c3a8daa0513de86ef2dacb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211290"
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a><span data-ttu-id="a3013-102">Nasıl yapılır: Değiştiricileri ve GenerateMember Özelliklerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="a3013-102">How to: Use the Modifiers and GenerateMember Properties</span></span>

<span data-ttu-id="a3013-103">Bir Windows formunda bir bileşen yerleştirdiğinizde, iki özellik tasarım ortamı tarafından sağlanan: `GenerateMember` ve `Modifiers`.</span><span class="sxs-lookup"><span data-stu-id="a3013-103">When you place a component on a Windows Form, two properties are provided by the design environment: `GenerateMember` and `Modifiers`.</span></span> <span data-ttu-id="a3013-104">`GenerateMember` Özellik belirtir, Windows Form Tasarımcısı ' bileşeni için bir üye değişkeni oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a3013-104">The `GenerateMember` property specifies when the Windows Forms Designer generates a member variable for a component.</span></span> <span data-ttu-id="a3013-105">`Modifiers` Özelliğidir, bu üye değişkenine atanan erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="a3013-105">The `Modifiers` property is the access modifier assigned to that member variable.</span></span> <span data-ttu-id="a3013-106">Varsa değerini `GenerateMember` özelliği `false`, değerini `Modifiers` özelliğinin hiçbir etkisi.</span><span class="sxs-lookup"><span data-stu-id="a3013-106">If the value of the `GenerateMember` property is `false`, the value of the `Modifiers` property has no effect.</span></span>

## <a name="specify-whether-a-component-is-a-member-of-the-form"></a><span data-ttu-id="a3013-107">Bir bileşen biçiminde bir üye mı olduğunu belirtin</span><span class="sxs-lookup"><span data-stu-id="a3013-107">Specify whether a component is a member of the form</span></span>

1. <span data-ttu-id="a3013-108">Visual Studio'da, Windows Form Tasarımcısı, formunuzu açın.</span><span class="sxs-lookup"><span data-stu-id="a3013-108">In Visual Studio, in the Windows Forms Designer, open your form.</span></span>

2. <span data-ttu-id="a3013-109">Açık **araç kutusu**ve üç form üzerinde yerleştirmek <xref:System.Windows.Forms.Button> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="a3013-109">Open the **Toolbox**, and on the form, place three <xref:System.Windows.Forms.Button> controls.</span></span>

3. <span data-ttu-id="a3013-110">Ayarlama `GenerateMember` ve `Modifiers` özellikleri her <xref:System.Windows.Forms.Button> aşağıdaki tabloya göre denetimi.</span><span class="sxs-lookup"><span data-stu-id="a3013-110">Set the `GenerateMember` and `Modifiers` properties for each <xref:System.Windows.Forms.Button> control according to the following table.</span></span>

    |<span data-ttu-id="a3013-111">Düğme adı</span><span class="sxs-lookup"><span data-stu-id="a3013-111">Button name</span></span>|<span data-ttu-id="a3013-112">GenerateMember değeri</span><span class="sxs-lookup"><span data-stu-id="a3013-112">GenerateMember value</span></span>|<span data-ttu-id="a3013-113">Değiştiriciler değeri</span><span class="sxs-lookup"><span data-stu-id="a3013-113">Modifiers value</span></span>|
    |-----------------|--------------------------|---------------------|
    |`button1`|`true`|`private`|
    |`button2`|`true`|`protected`|
    |`button3`|`false`|<span data-ttu-id="a3013-114">Değişiklik yok</span><span class="sxs-lookup"><span data-stu-id="a3013-114">No change</span></span>|

4. <span data-ttu-id="a3013-115">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a3013-115">Build the solution.</span></span>

5. <span data-ttu-id="a3013-116">İçinde **Çözüm Gezgini**, tıklayın **tüm dosyaları göster** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a3013-116">In **Solution Explorer**, click the **Show All Files** button.</span></span>

6. <span data-ttu-id="a3013-117">Açık **Form1** düğümünü ve **Kod Düzenleyicisi**açın **Form1.Designer.vb** veya **Form1.Designer.cs** dosya.</span><span class="sxs-lookup"><span data-stu-id="a3013-117">Open the **Form1** node, and in the **Code Editor**,open the **Form1.Designer.vb** or **Form1.Designer.cs** file.</span></span> <span data-ttu-id="a3013-118">Bu dosya Windows Forms Tasarımcısı tarafından yayılan kod içerir.</span><span class="sxs-lookup"><span data-stu-id="a3013-118">This file contains the code emitted by the Windows Forms Designer.</span></span>

7. <span data-ttu-id="a3013-119">Üç düğme için bildirimler bulun.</span><span class="sxs-lookup"><span data-stu-id="a3013-119">Find the declarations for the three buttons.</span></span> <span data-ttu-id="a3013-120">Aşağıdaki kod örneği tarafından belirtilen farklar gösterilmektedir `GenerateMember` ve `Modifiers` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="a3013-120">The following code example shows the differences specified by the `GenerateMember` and `Modifiers` properties.</span></span>

     [!code-csharp[System.Windows.Forms.GenerateMember#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]

     [!code-csharp[System.Windows.Forms.GenerateMember#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]

> [!NOTE]
> <span data-ttu-id="a3013-121">Varsayılan olarak, Windows Form Tasarımcısı atar `private` (`Friend` Visual Basic) değiştirici gibi kapsayıcı denetimlere <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="a3013-121">By default, the Windows Forms Designer assigns the `private` (`Friend` in Visual Basic) modifier to container controls like <xref:System.Windows.Forms.Panel>.</span></span> <span data-ttu-id="a3013-122">Varsa tabanınızı <xref:System.Windows.Forms.UserControl> veya <xref:System.Windows.Forms.Form> bir kapsayıcı denetimi sahip devralınan denetimler ve formları yeni alt öğe kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="a3013-122">If your base <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Form> has a container control, it will not accept new children in inherited controls and forms.</span></span> <span data-ttu-id="a3013-123">Temel bir kapsayıcı denetimin değiştiricisini çözümüdür `protected` veya `public`.</span><span class="sxs-lookup"><span data-stu-id="a3013-123">The solution is to change the modifier of the base container control to `protected` or `public`.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3013-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3013-124">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="a3013-125">Windows Forms Görsel Devralma</span><span class="sxs-lookup"><span data-stu-id="a3013-125">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
- [<span data-ttu-id="a3013-126">İzlenecek yol: Görsel devralmayı gösterme</span><span class="sxs-lookup"><span data-stu-id="a3013-126">Walkthrough: Demonstrating Visual Inheritance</span></span>](walkthrough-demonstrating-visual-inheritance.md)
- [<span data-ttu-id="a3013-127">Nasıl yapılır: Windows Form devralma</span><span class="sxs-lookup"><span data-stu-id="a3013-127">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
