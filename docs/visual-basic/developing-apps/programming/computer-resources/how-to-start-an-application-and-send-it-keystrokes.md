---
title: 'Nasıl Yapılır: Uygulama Başlatma ve Gönderme Tuş Vuruşları (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 716c88153ad01c7b225f31948c8aaaa2694dc512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582154"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="9aec0-102">Nasıl Yapılır: Uygulama Başlatma ve Gönderme Tuş Vuruşları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9aec0-102">How to: Start an Application and Send it Keystrokes (Visual Basic)</span></span>
<span data-ttu-id="9aec0-103">Bu örnekte `Shell` hesaplayıcı uygulamayı başlatmak için işlev ve iki sayının kullanarak tuş vuruşları göndererek çarpan `My.Computer.Keyboard.SendKeys` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9aec0-103">This example uses the `Shell` function to start the calculator application and then multiplies two numbers by sending keystrokes using the `My.Computer.Keyboard.SendKeys` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9aec0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9aec0-104">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="9aec0-105">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="9aec0-105">Robust Programming</span></span>  
 <span data-ttu-id="9aec0-106">A <xref:System.ArgumentException> istenen işlem tanıtıcısı olan bir uygulama bulunamazsa, özel durum oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="9aec0-106">A <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9aec0-107">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="9aec0-107">.NET Framework Security</span></span>  
 <span data-ttu-id="9aec0-108">Çağrı `Shell` işlevi tam güven gerektiren (<xref:System.Security.SecurityException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="9aec0-108">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aec0-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9aec0-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
