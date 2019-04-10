---
title: Sistem Bilgileri ve Windows Forms
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
ms.openlocfilehash: eeb469dbf4553634aa50d0a9ea17e9b2464defb4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228906"
---
# <a name="system-information-and-windows-forms"></a>Sistem Bilgileri ve Windows Forms
Bazen kodunuzda kararlar için uygulamanızın çalıştığı bilgisayar hakkında bilgi toplamak gereklidir. Örneğin, yalnızca belirli bir ağ etki alanına bağlı olduğunda geçerli olan bir işleve sahip olabilir; Bu durumda, etki alanı belirlemek ve etki alanı mevcut değilse işlev devre dışı bırakmak için bir yol gerekir.  
  
 Windows Forms uygulamaları kullanabilir <xref:System.Windows.Forms.SystemInformation> çalışma zamanında bir bilgisayar hakkında birkaç belirlemek için sınıf. Aşağıdaki örneği kullanarak göstermektedir <xref:System.Windows.Forms.SystemInformation> alınacak sınıfı <xref:System.Windows.Forms.SystemInformation.UserName%2A> ve <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to " _  
+ Domain)  
```  
  
 Tüm üyeleri <xref:System.Windows.Forms.SystemInformation> sınıfı salt okunur; bir kullanıcının ayarlarına değişiklik yapamazsınız. Her şeyi döndüren bilgi bilgisayara bağlı monitör sayısı 100'den fazla üye sınıfı yok (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) için Windows Gezgini'nde simgeler aralığını (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> ve <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).  
  
 Bazı üyeleri daha kullanışlı <xref:System.Windows.Forms.SystemInformation> sınıfını içeren <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, ve <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SystemInformation>
- [Windows Forms'ta Güç Yönetimi](power-management-in-windows-forms.md)
