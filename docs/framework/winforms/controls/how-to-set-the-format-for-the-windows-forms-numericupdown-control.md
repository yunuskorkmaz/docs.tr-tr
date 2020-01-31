---
title: NumericUpDown denetiminin biçimini ayarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 5ef1c801e96bef7b92e7e69dc36491144c456eeb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742179"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a><span data-ttu-id="828f7-102">Nasıl yapılır: Windows Forms NumericUpDown Denetiminin Biçimini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="828f7-102">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="828f7-103">Değerlerin Windows Forms <xref:System.Windows.Forms.NumericUpDown> denetiminde nasıl görüntüleneceğini yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="828f7-103">You can configure how values are displayed in the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="828f7-104"><xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> özelliği, ondalık ayırıcıdan sonra kaç sayının görüneceğini belirler; Varsayılan değer 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="828f7-104">The <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property determines how many numbers appear after the decimal point; the default is 0.</span></span> <span data-ttu-id="828f7-105"><xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> özelliği, her üç ondalık basamak arasına bir ayırıcının eklenip eklenmeyeceğini belirler; Varsayılan değer `false`.</span><span class="sxs-lookup"><span data-stu-id="828f7-105">The <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property determines whether a separator will be inserted between every three decimal digits; the default is `false`.</span></span> <span data-ttu-id="828f7-106"><xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> özelliği `true`olarak ayarlandıysa, denetim değeri onlu biçim yerine onaltılık olarak görüntüleyebilir. Varsayılan değer `false`.</span><span class="sxs-lookup"><span data-stu-id="828f7-106">The control can display values in hexadecimal instead of decimal format, if the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property is set to `true`; the default is `false`.</span></span>  
  
### <a name="to-format-the-numeric-value"></a><span data-ttu-id="828f7-107">Sayısal değeri biçimlendirmek için</span><span class="sxs-lookup"><span data-stu-id="828f7-107">To format the numeric value</span></span>  
  
- <span data-ttu-id="828f7-108"><xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> özelliğini bir tamsayı olarak ayarlayıp <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> özelliğini `true` veya `false`olarak ayarlayarak ondalık değeri görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="828f7-108">Display a decimal value by setting the <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property to an integer and setting the <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property to `true` or `false`.</span></span>  
  
    ```vb  
    NumericUpDown1.DecimalPlaces = 2  
    NumericUpDown1.ThousandsSeparator = True  
    ```  
  
    ```csharp  
    numericUpDown1.DecimalPlaces = 2;  
    numericUpDown1.ThousandsSeparator = true;  
    ```  
  
    ```cpp  
    numericUpDown1->DecimalPlaces = 2;  
    numericUpDown1->ThousandsSeparator = true;  
    ```  
  
     <span data-ttu-id="828f7-109">veya</span><span class="sxs-lookup"><span data-stu-id="828f7-109">-or-</span></span>  
  
- <span data-ttu-id="828f7-110"><xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> özelliğini `true`olarak ayarlayarak onaltılık bir değer görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="828f7-110">Display a hexadecimal value by setting the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property to `true`.</span></span>  
  
    ```vb  
    NumericUpDown1.Hexadecimal = True  
    ```  
  
    ```csharp  
    numericUpDown1.Hexadecimal = true;  
    ```  
  
    ```cpp  
    numericUpDown1->Hexadecimal = true;  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="828f7-111">Değer formda onaltılı olarak görüntülense bile, <xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliği üzerinde gerçekleştirdiğiniz tüm testler, onun ondalık değerini test eder.</span><span class="sxs-lookup"><span data-stu-id="828f7-111">Even if the value is displayed on the form as hexadecimal, any tests you perform on the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property will be testing its decimal value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="828f7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="828f7-112">See also</span></span>

- <xref:System.Windows.Forms.NumericUpDown>
- [<span data-ttu-id="828f7-113">NumericUpDown Denetimi</span><span class="sxs-lookup"><span data-stu-id="828f7-113">NumericUpDown Control</span></span>](numericupdown-control-windows-forms.md)
- [<span data-ttu-id="828f7-114">NumericUpDown Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="828f7-114">NumericUpDown Control Overview</span></span>](numericupdown-control-overview-windows-forms.md)
