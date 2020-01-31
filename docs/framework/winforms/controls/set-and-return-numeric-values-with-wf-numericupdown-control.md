---
title: NumericUpDown denetimiyle sayısal değerleri ayarlama ve döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric values [Windows Forms], Windows Forms
- Windows Forms, numeric values
- Windows Forms controls, NumericUpDown
- NumericUpDown control [Windows Forms], setting and returning values
ms.assetid: 5bd8f8cd-4c12-49ea-9cc3-2a647d064689
ms.openlocfilehash: a0b264fec9619b467c293bcb96278c4517775ac3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743028"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a><span data-ttu-id="a1894-102">Nasıl yapılır: Windows Forms NumericUpDown Denetimi ile Sayı Değerleri Ayarlama ve Döndürme</span><span class="sxs-lookup"><span data-stu-id="a1894-102">How to: Set and Return Numeric Values with the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="a1894-103">Windows Forms <xref:System.Windows.Forms.NumericUpDown> denetiminin sayısal değeri <xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliğine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="a1894-103">The numeric value of the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control is determined by its <xref:System.Windows.Forms.NumericUpDown.Value%2A> property.</span></span> <span data-ttu-id="a1894-104">Denetimin değeri için diğer tüm özellikler gibi koşullu testler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1894-104">You can write conditional tests for the control's value just as with any other property.</span></span> <span data-ttu-id="a1894-105"><xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliği ayarlandıktan sonra, bu işlemi gerçekleştirmek için kod yazarak doğrudan ayarlayabilir veya <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> ve <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> yöntemlerini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1894-105">Once the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property is set, you can adjust it directly by writing code to perform operations on it, or you can call the <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> and <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> methods.</span></span>  
  
### <a name="to-set-the-numeric-value"></a><span data-ttu-id="a1894-106">Sayısal değeri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a1894-106">To set the numeric value</span></span>  
  
1. <span data-ttu-id="a1894-107">Koddaki <xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliğine veya Özellikler penceresi bir değer atayın.</span><span class="sxs-lookup"><span data-stu-id="a1894-107">Assign a value to the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property in code or in the Properties window.</span></span>  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     <span data-ttu-id="a1894-108">veya</span><span class="sxs-lookup"><span data-stu-id="a1894-108">-or-</span></span>  
  
2. <span data-ttu-id="a1894-109">Değeri <xref:System.Windows.Forms.NumericUpDown.Increment%2A> özelliğinde belirtilen miktara göre artırmak veya azaltmak için <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> veya <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="a1894-109">Call the <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> or <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> method to increase or decrease the value by the amount specified in the <xref:System.Windows.Forms.NumericUpDown.Increment%2A> property.</span></span>  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a><span data-ttu-id="a1894-110">Sayısal değeri döndürmek için</span><span class="sxs-lookup"><span data-stu-id="a1894-110">To return the numeric value</span></span>  
  
- <span data-ttu-id="a1894-111">Koddaki <xref:System.Windows.Forms.NumericUpDown.Value%2A> özelliğine erişin.</span><span class="sxs-lookup"><span data-stu-id="a1894-111">Access the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property in code.</span></span>  
  
    ```vb  
    If NumericUpDown1.Value >= 65 Then  
       MessageBox.Show("Age is: " & NumericUpDown1.Value.ToString)  
    Else  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.")  
    End If  
    ```  
  
    ```csharp  
    if(numericUpDown1.Value >= 65)  
    {  
       MessageBox.Show("Age is: " + numericUpDown1.Value.ToString());  
    }  
    else  
    {  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
    ```cpp  
    if(numericUpDown1->Value >= 65)  
    {  
       MessageBox::Show(String::Concat("Age is: ",  
          numericUpDown1->Value.ToString()));  
    }  
    else  
    {  
       MessageBox::Show  
          ("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a1894-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1894-112">See also</span></span>

- <xref:System.Windows.Forms.NumericUpDown>
- <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a1894-113">NumericUpDown Denetimi</span><span class="sxs-lookup"><span data-stu-id="a1894-113">NumericUpDown Control</span></span>](numericupdown-control-windows-forms.md)
- [<span data-ttu-id="a1894-114">NumericUpDown Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a1894-114">NumericUpDown Control Overview</span></span>](numericupdown-control-overview-windows-forms.md)
