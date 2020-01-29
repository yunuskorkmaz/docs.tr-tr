---
title: Sistem Bilgileri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- domain names [Windows Forms], retrieving
- SystemInformation class [Windows Forms]
- user names [Windows Forms], retrieving
- system information [Windows Forms]
ms.assetid: 30cf43a3-8cb2-4ff3-862b-6c34576616a8
ms.openlocfilehash: a91e2fd8db0ef338ce30f89f11869f1b6698af3b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732584"
---
# <a name="system-information-and-windows-forms"></a><span data-ttu-id="17bf8-102">Sistem Bilgileri ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="17bf8-102">System Information and Windows Forms</span></span>
<span data-ttu-id="17bf8-103">Bazen kodunuzda kararlar almak için uygulamanızın üzerinde çalıştığı bilgisayar hakkında bilgi toplamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="17bf8-103">Sometimes it is necessary to gather information about the computer that your application is running on in order to make decisions in your code.</span></span> <span data-ttu-id="17bf8-104">Örneğin, yalnızca belirli bir ağ etki alanına bağlı olduğunda uygulanabilen bir işleviniz olabilir; Bu durumda, etki alanını belirlemenin ve etki alanı yoksa işlevi devre dışı bırakabilmeniz için bir yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="17bf8-104">For example, you might have a function that is only applicable when connected to a particular network domain; in this case you would need a way to determine the domain and disable the function if the domain is not present.</span></span>  
  
 <span data-ttu-id="17bf8-105">Windows Forms uygulamalar, çalışma zamanında bir bilgisayar hakkında birkaç şeyi belirleyebilmek için <xref:System.Windows.Forms.SystemInformation> sınıfını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="17bf8-105">Windows Forms applications can use the <xref:System.Windows.Forms.SystemInformation> class to determine a number of things about a computer at run time.</span></span> <span data-ttu-id="17bf8-106">Aşağıdaki örnek, <xref:System.Windows.Forms.SystemInformation.UserName%2A> ve <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>almak için <xref:System.Windows.Forms.SystemInformation> sınıfını kullanmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="17bf8-106">The following example demonstrates using the <xref:System.Windows.Forms.SystemInformation> class to retrieve the <xref:System.Windows.Forms.SystemInformation.UserName%2A> and <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span></span>  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to "
+ Domain);
```  
  
 <span data-ttu-id="17bf8-107"><xref:System.Windows.Forms.SystemInformation> sınıfının tüm üyeleri salt okunurdur; bir kullanıcının ayarlarını değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="17bf8-107">All members of the <xref:System.Windows.Forms.SystemInformation> class are read-only; you cannot modify a user's settings.</span></span> <span data-ttu-id="17bf8-108">Sınıfın 100 üzerinde bir üyesi vardır ve bilgisayara eklenen izleyici sayısından (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) Windows Gezgini 'nde (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> ve <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>) simgelerin sonuna kadar her şeye bilgi döndürülüyor.</span><span class="sxs-lookup"><span data-stu-id="17bf8-108">There are over 100 members of the class, returning information on everything from the number of monitors attached to the computer (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) to the spacing of icons in Windows Explorer (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> and <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span></span>  
  
 <span data-ttu-id="17bf8-109"><xref:System.Windows.Forms.SystemInformation> sınıfının daha yararlı üyelerinden bazıları <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>ve <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>içerir.</span><span class="sxs-lookup"><span data-stu-id="17bf8-109">Some of the more useful members of the <xref:System.Windows.Forms.SystemInformation> class include <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, and <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17bf8-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17bf8-110">See also</span></span>

- <xref:System.Windows.Forms.SystemInformation>
- [<span data-ttu-id="17bf8-111">Windows Forms'ta Güç Yönetimi</span><span class="sxs-lookup"><span data-stu-id="17bf8-111">Power Management in Windows Forms</span></span>](power-management-in-windows-forms.md)
