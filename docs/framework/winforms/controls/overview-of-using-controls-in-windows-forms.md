---
title: Windows Forms'ta Denetimlerin Kullanımına Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, controls
- controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: fddbe951-4485-459d-a5fd-665ea346dbc1
ms.openlocfilehash: e8ae5ec00ee488f0b7400bfa99483c4efc29e016
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703250"
---
# <a name="overview-of-using-controls-in-windows-forms"></a><span data-ttu-id="1cf2c-102">Windows Forms'ta Denetimlerin Kullanımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1cf2c-102">Overview of Using Controls in Windows Forms</span></span>
<span data-ttu-id="1cf2c-103">Bu konu, bir Windows Forms uygulaması temel öğelerini açıklar ve denetimlerini kullanır ve bir Windows Forms uygulamasında olayları işleyen basit bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="1cf2c-103">This topic describes the essential elements of a Windows Forms application and provides a simple example that uses controls and handles events in a Windows Forms application.</span></span>  
  
## <a name="simple-windows-forms-applications"></a><span data-ttu-id="1cf2c-104">Basit bir Windows Forms uygulamaları</span><span class="sxs-lookup"><span data-stu-id="1cf2c-104">Simple Windows Forms Applications</span></span>  
 <span data-ttu-id="1cf2c-105">En az bir Windows Forms uygulaması aşağıdaki öğelerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="1cf2c-105">At a minimum, a Windows Forms application consists of the following elements:</span></span>  
  
-   <span data-ttu-id="1cf2c-106">Öğesinden türetilen bir veya daha fazla sınıf <xref:System.Windows.Forms.Form?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1cf2c-106">One or more classes that derive from <xref:System.Windows.Forms.Form?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="1cf2c-107">A `Main` çağıran yöntem `static` (`shared` Visual Basic'te) <xref:System.Windows.Forms.Application.Run%2A> yöntemi ve geçişleri bir <xref:System.Windows.Forms.Form> ona örneği.</span><span class="sxs-lookup"><span data-stu-id="1cf2c-107">A `Main` method that invokes the `static` (`shared` in Visual Basic) <xref:System.Windows.Forms.Application.Run%2A> method and passes a <xref:System.Windows.Forms.Form> instance to it.</span></span> <span data-ttu-id="1cf2c-108"><xref:System.Windows.Forms.Application.Run%2A> Yöntemi uygulama işletim sisteminden iletileri işler.</span><span class="sxs-lookup"><span data-stu-id="1cf2c-108">The <xref:System.Windows.Forms.Application.Run%2A> method processes messages from the operating system to the application.</span></span>  
  
 <span data-ttu-id="1cf2c-109">Aşağıdaki kod örneği, bir Windows Forms uygulaması temel öğelerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1cf2c-109">The following code example shows the essential elements of a Windows Forms application.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
  
Public Class MyForm  
   Inherits Form  
  
   Public Sub New()  
      Me.Text = "Hello World"  
   End Sub 'New  
  
   <STAThread()> _  
   Public Shared Sub Main()  
      Dim aform As New MyForm()  
      ' The Application.Run method processes messages from the operating system   
      ' to your application. If you comment out the next line of code,   
      ' your application will compile and execute, but because it is not in the  
      ' message loop, it will exit after an instance of the form is created.  
      Application.Run(aform)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
  
public class MyForm : Form {  
  
   public MyForm() {  
      this.Text = "Hello World";  
   }  
   [STAThread]  
   public static void Main(string[] args) {  
     MyForm aform = new MyForm();  
// The Application.Run method processes messages from the operating system   
// to your application. If you comment out the next line of code,   
// your application will compile and execute, but because it is not in the // message loop, it will exit after an instance of the form is created.  
      Application.Run(aform);  
   }  
}  
```  
  
## <a name="using-controls-in-a-windows-forms-application"></a><span data-ttu-id="1cf2c-110">Bir Windows Forms uygulamasında denetimlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="1cf2c-110">Using Controls in a Windows Forms Application</span></span>  
 <span data-ttu-id="1cf2c-111">Aşağıdaki kod örneği, Windows Forms uygulamaları nasıl denetimlerini kullanın ve olayları işlemek gösteren basit bir uygulamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1cf2c-111">The following code example shows a simple application that illustrates how Windows Forms applications use controls and handle events.</span></span> <span data-ttu-id="1cf2c-112">Formdaki üç düğme örnek oluşur; Her düğme tıklandığında arka plan rengini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="1cf2c-112">The example consists of three buttons on a form; each button changes the background color when clicked.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.ComponentModel  
Imports System.Windows.Forms  
Imports System.Resources  
Imports System.Drawing  
  
Public Class MyForm  
   Inherits Form  
   Private red As Button  
   Private blue As Button  
   Private green As Button  
  
   Public Sub New()  
      InitializeComponent()  
   End Sub  
  
   Protected Overloads Overrides Sub Dispose(disposing as Boolean)  
      MyBase.Dispose(disposing)  
   End Sub  
  
   ' InitializeComponent is a helper method for the constructor.   
   ' It is included for consistency with code that is   
   ' auto-generated by the Windows Forms designer in Visual Studio.   
   Private Sub InitializeComponent()  
  
      ' Creates three buttons, sets their properties, and attaches  
      ' an event handler to each button.  
      red = New Button()  
      red.Text = "Red"  
      red.Location = New Point(100, 50)  
      red.Size = New Size(50, 50)  
      AddHandler red.Click, AddressOf button_Click  
      Controls.Add(red)  
  
      blue = New Button()  
      blue.Text = "Blue"  
      blue.Location = New Point(100, 100)  
      blue.Size = New Size(50, 50)  
      AddHandler blue.Click, AddressOf button_Click  
      Controls.Add(blue)  
  
      green = New Button()  
      green.Text = "Green"  
      green.Location = New Point(100, 150)  
      green.Size = New Size(50, 50)  
      AddHandler green.Click, AddressOf button_Click  
      Controls.Add(green)  
   End Sub  
  
   ' Event handler.  
   Private Sub button_Click(sender As Object, e As EventArgs)  
      If sender Is red Then  
         Me.BackColor = Color.Red  
      Else  
         If sender Is blue Then  
            Me.BackColor = Color.Blue  
         Else  
            Me.BackColor = Color.Green  
         End If  
      End If   
   End Sub  
  
   ' The STAThreadAttribute informs the common language runtime that  
   ' Windows Forms uses the single-threaded apartment model.  
   <STAThread()> _  
   Public Shared Sub Main()  
      Application.Run(New MyForm())  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.ComponentModel;  
using System.Windows.Forms;  
using System.Resources;  
using System.Drawing;  
  
public class MyForm : Form {  
   private Button red;  
   private Button blue;  
   private Button green;  
  
   public MyForm() : base() {     
      InitializeComponent();     
   }  
  
   protected override void Dispose(bool disposing) {  
      base.Dispose(disposing);  
   }  
  
// InitializeComponent is a helper method for the constructor.   
// It is included for consistency with code that is   
// auto-generated by the Windows Forms designer in Visual Studio.   
   private void InitializeComponent() {  
  
// A delegate for the click event of a button. The argument to   
// the constructor contains a reference to the method that performs the   
// event handling logic.  
      EventHandler handler = new EventHandler(button_Click);  
  
// Creates three buttons, sets their properties, and attaches  
// an event handler to each button.  
  
      red = new Button();  
      red.Text = "Red";  
      red.Location = new Point(100, 50);  
      red.Size = new Size(50, 50);  
      red.Click +=handler;  
      Controls.Add(red);  
  
      blue = new Button();  
      blue.Text = "Blue";  
      blue.Location = new Point(100, 100);  
      blue.Size = new Size(50, 50);  
      blue.Click += handler;  
      Controls.Add(blue);  
  
      green = new Button();  
      green.Text = "Green";  
      green.Location = new Point(100, 150);  
      green.Size = new Size(50, 50);  
      green.Click += handler;  
      Controls.Add(green);        
      }  
  
   // Event handler.  
   private void button_Click(object sender, EventArgs e) {  
            if (sender == red) this.BackColor = Color.Red ;  
                  else if (sender == blue) this.BackColor = Color.Blue;  
                  else this.BackColor = Color.Green;  
        }  
   // The STAThreadAttribute informs the common language runtime that  
   // Windows Forms uses the single-threaded apartment model.  
  [STAThread]  
   public static void Main(string[] args) {  
   Application.Run(new MyForm());  
   }  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1cf2c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cf2c-113">See also</span></span>
- [<span data-ttu-id="1cf2c-114">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="1cf2c-114">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="1cf2c-115">Windows Forms Denetimi Geliştirmenin Esasları</span><span class="sxs-lookup"><span data-stu-id="1cf2c-115">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)
