---
title: 'Nasıl yapılır: Windows Forms NumericUpDown Denetiminin Biçimini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 6db7a1b2aeb7282c3ac827cb8319706ed348fc22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949157"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a><span data-ttu-id="deda3-102">Nasıl yapılır: Windows Forms NumericUpDown Denetiminin Biçimini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="deda3-102">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="deda3-103">Windows Forms <xref:System.Windows.Forms.NumericUpDown> denetiminde değerlerin nasıl görüntüleneceğini yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="deda3-103">You can configure how values are displayed in the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="deda3-104"><xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> Özelliği, ondalık ayırıcıdan sonra kaç sayının görüneceğini belirler; varsayılan değer 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="deda3-104">The <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property determines how many numbers appear after the decimal point; the default is 0.</span></span> <span data-ttu-id="deda3-105">Özelliği, her üç ondalık basamak arasına bir ayırıcının eklenip eklenmeyeceğini belirler; varsayılan değer `false`. <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A></span><span class="sxs-lookup"><span data-stu-id="deda3-105">The <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property determines whether a separator will be inserted between every three decimal digits; the default is `false`.</span></span> <span data-ttu-id="deda3-106"><xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> Özelliği `false`olarak `true`ayarlandıysa, denetim değeri ondalık biçimi yerine onaltılı olarak görüntülenebilir; varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="deda3-106">The control can display values in hexadecimal instead of decimal format, if the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property is set to `true`; the default is `false`.</span></span>  
  
### <a name="to-format-the-numeric-value"></a><span data-ttu-id="deda3-107">Sayısal değeri biçimlendirmek için</span><span class="sxs-lookup"><span data-stu-id="deda3-107">To format the numeric value</span></span>  
  
- <span data-ttu-id="deda3-108"><xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> Özelliği bir tamsayı olarak ayarlayıp veya <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> `true` `false`olarak ayarlayarak ondalık değeri görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="deda3-108">Display a decimal value by setting the <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property to an integer and setting the <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property to `true` or `false`.</span></span>  
  
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
  
     <span data-ttu-id="deda3-109">-veya-</span><span class="sxs-lookup"><span data-stu-id="deda3-109">-or-</span></span>  
  
- <span data-ttu-id="deda3-110"><xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> Özelliğini olarak`true`ayarlayarak onaltılık bir değer görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="deda3-110">Display a hexadecimal value by setting the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property to `true`.</span></span>  
  
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
    > <span data-ttu-id="deda3-111">Değer formda onaltılı olarak gösterilse bile, <xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliği üzerinde gerçekleştirdiğiniz tüm testler, ondalık değerini test eder.</span><span class="sxs-lookup"><span data-stu-id="deda3-111">Even if the value is displayed on the form as hexadecimal, any tests you perform on the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property will be testing its decimal value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deda3-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="deda3-112">See also</span></span>

- <xref:System.Windows.Forms.NumericUpDown>
- [<span data-ttu-id="deda3-113">NumericUpDown Denetimi</span><span class="sxs-lookup"><span data-stu-id="deda3-113">NumericUpDown Control</span></span>](numericupdown-control-windows-forms.md)
- [<span data-ttu-id="deda3-114">NumericUpDown Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="deda3-114">NumericUpDown Control Overview</span></span>](numericupdown-control-overview-windows-forms.md)
