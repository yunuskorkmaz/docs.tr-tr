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
# <a name="system-information-and-windows-forms"></a>Sistem Bilgileri ve Windows Forms
Bazen kodunuzda kararlar almak için uygulamanızın üzerinde çalıştığı bilgisayar hakkında bilgi toplamak gereklidir. Örneğin, yalnızca belirli bir ağ etki alanına bağlı olduğunda uygulanabilen bir işleviniz olabilir; Bu durumda, etki alanını belirlemenin ve etki alanı yoksa işlevi devre dışı bırakabilmeniz için bir yol gerekir.  
  
 Windows Forms uygulamalar, çalışma zamanında bir bilgisayar hakkında birkaç şeyi belirleyebilmek için <xref:System.Windows.Forms.SystemInformation> sınıfını kullanabilir. Aşağıdaki örnek, <xref:System.Windows.Forms.SystemInformation.UserName%2A> ve <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>almak için <xref:System.Windows.Forms.SystemInformation> sınıfını kullanmayı gösterir:  
  
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
  
 <xref:System.Windows.Forms.SystemInformation> sınıfının tüm üyeleri salt okunurdur; bir kullanıcının ayarlarını değiştiremezsiniz. Sınıfın 100 üzerinde bir üyesi vardır ve bilgisayara eklenen izleyici sayısından (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) Windows Gezgini 'nde (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> ve <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>) simgelerin sonuna kadar her şeye bilgi döndürülüyor.  
  
 <xref:System.Windows.Forms.SystemInformation> sınıfının daha yararlı üyelerinden bazıları <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>ve <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>içerir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SystemInformation>
- [Windows Forms'ta Güç Yönetimi](power-management-in-windows-forms.md)
