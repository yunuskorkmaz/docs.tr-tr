---
title: 'Nasıl yapılır: Denetim İşleme Sınıfı Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- visual themes [Windows Forms], applying to Windows Forms controls
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
ms.openlocfilehash: 7115c227cb24cf12a50073d0dc587524abf0cbb9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785846"
---
# <a name="how-to-use-a-control-rendering-class"></a><span data-ttu-id="53bec-102">Nasıl yapılır: Denetim İşleme Sınıfı Kullanma</span><span class="sxs-lookup"><span data-stu-id="53bec-102">How to: Use a Control Rendering Class</span></span>
<span data-ttu-id="53bec-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Forms.ComboBoxRenderer> aşağı açılan okunu bir birleşik giriş kutusu denetimi oluşturmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="53bec-103">This example demonstrates how to use the <xref:System.Windows.Forms.ComboBoxRenderer> class to render the drop-down arrow of a combo box control.</span></span> <span data-ttu-id="53bec-104">Örnek oluşan <xref:System.Windows.Forms.Control.OnPaint%2A> basit bir özel denetimin yöntemi.</span><span class="sxs-lookup"><span data-stu-id="53bec-104">The example consists of the <xref:System.Windows.Forms.Control.OnPaint%2A> method of a simple custom control.</span></span> <span data-ttu-id="53bec-105"><xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> Özelliği görsel stiller uygulama windows istemci alanında etkin olup olmadığını belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53bec-105">The <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> property is used to determine whether visual styles are enabled in the client area of application windows.</span></span> <span data-ttu-id="53bec-106">Görsel stillerin etkin olması durumunda sonra <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> yöntemi açılan liste okunu görsel stilde; işleme Aksi takdirde <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> yöntemi Klasik Windows stili açılan oka işleme.</span><span class="sxs-lookup"><span data-stu-id="53bec-106">If visual styles are active, then the <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> method will render the drop-down arrow with visual styles; otherwise, the <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> method will render the drop-down arrow in the classic Windows style.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53bec-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="53bec-107">Example</span></span>  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="53bec-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="53bec-108">Compiling the Code</span></span>  
 <span data-ttu-id="53bec-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="53bec-109">This example requires:</span></span>  
  
- <span data-ttu-id="53bec-110">Öğesinden türetilen özel denetim <xref:System.Windows.Forms.Control> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53bec-110">A custom control derived from the <xref:System.Windows.Forms.Control> class.</span></span>  
  
- <span data-ttu-id="53bec-111">A <xref:System.Windows.Forms.Form> özel denetimi barındıran.</span><span class="sxs-lookup"><span data-stu-id="53bec-111">A <xref:System.Windows.Forms.Form> that hosts the custom control.</span></span>  
  
- <span data-ttu-id="53bec-112">Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, ve <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="53bec-112">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53bec-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53bec-113">See also</span></span>

- [<span data-ttu-id="53bec-114">Denetimleri Görsel Stilde İşleme</span><span class="sxs-lookup"><span data-stu-id="53bec-114">Rendering Controls with Visual Styles</span></span>](rendering-controls-with-visual-styles.md)
