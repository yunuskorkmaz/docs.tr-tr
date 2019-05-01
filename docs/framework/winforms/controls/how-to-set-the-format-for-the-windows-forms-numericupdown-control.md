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
ms.openlocfilehash: 5957a44c7b07aa1b8d8df32667f023c0873ec1de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013198"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a><span data-ttu-id="71e07-102">Nasıl yapılır: Windows Forms NumericUpDown Denetiminin Biçimini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="71e07-102">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="71e07-103">Windows Forms'ta değerlerin nasıl görüntüleneceğini yapılandırabileceğiniz <xref:System.Windows.Forms.NumericUpDown> denetimi.</span><span class="sxs-lookup"><span data-stu-id="71e07-103">You can configure how values are displayed in the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="71e07-104"><xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> Özelliği belirler kaç sayılar ondalık ayırıcıdan sonra görünür; varsayılan değer 0'dır.</span><span class="sxs-lookup"><span data-stu-id="71e07-104">The <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property determines how many numbers appear after the decimal point; the default is 0.</span></span> <span data-ttu-id="71e07-105"><xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> Varsayılan özellik, her üç ondalık basamak arasında bir ayırıcı eklenip eklenmeyeceğini belirler; `false`.</span><span class="sxs-lookup"><span data-stu-id="71e07-105">The <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property determines whether a separator will be inserted between every three decimal digits; the default is `false`.</span></span> <span data-ttu-id="71e07-106">Denetim değerleri yerine ondalık, onaltılık görüntüleyebilirsiniz <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> özelliği `true`; varsayılan `false`.</span><span class="sxs-lookup"><span data-stu-id="71e07-106">The control can display values in hexadecimal instead of decimal format, if the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property is set to `true`; the default is `false`.</span></span>  
  
### <a name="to-format-the-numeric-value"></a><span data-ttu-id="71e07-107">Sayısal değerini biçimlendirmek için</span><span class="sxs-lookup"><span data-stu-id="71e07-107">To format the numeric value</span></span>  
  
- <span data-ttu-id="71e07-108">Bir ondalık değer ayarlayarak görüntüleyin <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> özelliği bir tamsayı ve ayarı <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> özelliğini `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="71e07-108">Display a decimal value by setting the <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property to an integer and setting the <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property to `true` or `false`.</span></span>  
  
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
  
     <span data-ttu-id="71e07-109">-veya-</span><span class="sxs-lookup"><span data-stu-id="71e07-109">-or-</span></span>  
  
- <span data-ttu-id="71e07-110">Ayarlayarak bir onaltılık değer görüntüleme <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="71e07-110">Display a hexadecimal value by setting the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property to `true`.</span></span>  
  
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
    >  <span data-ttu-id="71e07-111">Değeri, onaltılık olarak formda görüntülenir bile herhangi bir test gerçekleştirdiğiniz <xref:System.Windows.Forms.NumericUpDown.Value%2A> özellik ondalık değeri test.</span><span class="sxs-lookup"><span data-stu-id="71e07-111">Even if the value is displayed on the form as hexadecimal, any tests you perform on the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property will be testing its decimal value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71e07-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71e07-112">See also</span></span>

- <xref:System.Windows.Forms.NumericUpDown>
- [<span data-ttu-id="71e07-113">NumericUpDown Denetimi</span><span class="sxs-lookup"><span data-stu-id="71e07-113">NumericUpDown Control</span></span>](numericupdown-control-windows-forms.md)
- [<span data-ttu-id="71e07-114">NumericUpDown Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="71e07-114">NumericUpDown Control Overview</span></span>](numericupdown-control-overview-windows-forms.md)
