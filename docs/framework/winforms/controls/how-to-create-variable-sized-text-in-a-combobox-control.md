---
title: 'Nasıl yapılır: ComboBox Denetiminde Değişken Boyutlu Metin Oluşturma'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- text [Windows Forms], drawing in combo boxes
- examples [Windows Forms], ComboBox control
- combo boxes [Windows Forms], drawing text
- ComboBox control [Windows Forms], examples [C#]
- ComboBox control [Windows Forms], drawing custom text
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
ms.openlocfilehash: 9155893b3d47707e0e55ee33e30d7998654f9e93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085616"
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a><span data-ttu-id="a837b-102">Nasıl yapılır: ComboBox Denetiminde Değişken Boyutlu Metin Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a837b-102">How to: Create Variable Sized Text in a ComboBox Control</span></span>
<span data-ttu-id="a837b-103">Bu örnek özel çizim metin gösterir bir <xref:System.Windows.Forms.ComboBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="a837b-103">This example demonstrates custom drawing of text in a <xref:System.Windows.Forms.ComboBox> control.</span></span> <span data-ttu-id="a837b-104">Bir öğenin belirli bir ölçütü karşıladığında bir büyük yazı tipiyle çizilmiş ve kırmızı açık.</span><span class="sxs-lookup"><span data-stu-id="a837b-104">When an item meets a certain criteria, it is drawn in a larger font and turned red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a837b-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a837b-105">Example</span></span>  
  
```vb  
Private Sub ComboBox1_MeasureItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.MeasureItemEventArgs) Handles ComboBox1.MeasureItem  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
    Dim siText As SizeF  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), _  
lFont)  
    Else  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), bFont)  
    End If  
  
    e.ItemHeight = siText.Height  
    e.ItemWidth = siText.Width  
End Sub  
  
Private Sub ComboBox1_DrawItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.DrawItemEventArgs) Handles ComboBox1.DrawItem  
    Dim g As Graphics = e.Graphics  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        g.DrawString(ComboBox1.Items.Item(e.Index), lfont, Brushes.Red, _  
e.Bounds.X, e.Bounds.Y)  
    Else  
        g.DrawString(ComboBox1.Items.Item(e.Index), bFont, Brushes.Black, e.Bounds.X, e.Bounds.Y)  
    End If  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a837b-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a837b-106">Compiling the Code</span></span>  
 <span data-ttu-id="a837b-107">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a837b-107">This example requires:</span></span>  
  
-   <span data-ttu-id="a837b-108">Bir Windows formu.</span><span class="sxs-lookup"><span data-stu-id="a837b-108">A Windows form.</span></span>  
  
-   <span data-ttu-id="a837b-109">A <xref:System.Windows.Forms.ComboBox> adlı Denetim `ListBox1` üç öğelerle <xref:System.Windows.Forms.ComboBox.Items%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a837b-109">A <xref:System.Windows.Forms.ComboBox> control named `ListBox1` with three items in the <xref:System.Windows.Forms.ComboBox.Items%2A> property.</span></span> <span data-ttu-id="a837b-110">Bu örnekte, üç öğeye adlandırılır `"One", Two", and Three"`.</span><span class="sxs-lookup"><span data-stu-id="a837b-110">In this example, the three items are named `"One", Two", and Three"`.</span></span> <span data-ttu-id="a837b-111"><xref:System.Windows.Forms.ComboBox.DrawMode%2A> Özelliği `ComboBox1` ayarlanmalıdır <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.</span><span class="sxs-lookup"><span data-stu-id="a837b-111">The <xref:System.Windows.Forms.ComboBox.DrawMode%2A> property of `ComboBox1` must be set to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a837b-112">Bu teknik de geçerlidir <xref:System.Windows.Forms.ListBox> denetim — yerini alabilecek bir <xref:System.Windows.Forms.ListBox> için <xref:System.Windows.Forms.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="a837b-112">This technique is also applicable to the <xref:System.Windows.Forms.ListBox> control — you can substitute a <xref:System.Windows.Forms.ListBox> for the <xref:System.Windows.Forms.ComboBox>.</span></span>  
  
-   <span data-ttu-id="a837b-113">Başvurular <xref:System.Windows.Forms?displayProperty=nameWithType> ve <xref:System.Drawing?displayProperty=nameWithType> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="a837b-113">References to the <xref:System.Windows.Forms?displayProperty=nameWithType> and <xref:System.Drawing?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a837b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a837b-114">See also</span></span>

- <xref:System.Windows.Forms.ComboBox.DrawItem>
- <xref:System.Windows.Forms.DrawItemEventArgs>
- <xref:System.Windows.Forms.ComboBox.MeasureItem>
- [<span data-ttu-id="a837b-115">Yerleşik Sahip Çizimi Destekli Denetimler</span><span class="sxs-lookup"><span data-stu-id="a837b-115">Controls with Built-In Owner-Drawing Support</span></span>](controls-with-built-in-owner-drawing-support.md)
- [<span data-ttu-id="a837b-116">ListBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="a837b-116">ListBox Control</span></span>](listbox-control-windows-forms.md)
- [<span data-ttu-id="a837b-117">ComboBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="a837b-117">ComboBox Control</span></span>](combobox-control-windows-forms.md)
