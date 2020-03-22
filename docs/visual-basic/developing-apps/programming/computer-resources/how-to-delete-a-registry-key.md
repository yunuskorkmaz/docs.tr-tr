---
title: 'Nasıl Yapılır: Kayıt Defteri Anahtarını Silme'
ms.date: 07/20/2015
f1_keywords:
- vb.DeleteSetting
helpviewer_keywords:
- GetSetting function [Visual Basic]
- registry [Visual Basic], deleting values
- GetAllSettings function
- registry keys [Visual Basic], deleting
- registry [Visual Basic], deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
ms.openlocfilehash: f38301a3a717a35b98e55804d6435d046bbbbab4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345647"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarını Silme

Ve <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> yöntemler kayıt defteri anahtarlarını silmek için kullanılabilir.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-delete-a-registry-key"></a>Kayıt defteri anahtarını silmek için  
  
- Kayıt `DeleteSubKey` defteri anahtarını silmek için yöntemi kullanın. Bu örnek, CurrentUser kovanındaki anahtar Yazılım/TestApp'i siler. Koddaki bu durumu uygun dizeyle değiştirebilir veya kullanıcı tarafından sağlanan bilgilere güvendirebilirsiniz.  
  
     [!code-vb[VbResourceTasks#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Anahtar/değer `DeleteSubKey` çifti yoksa yöntem boş bir dize döndürür.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Anahtarın adı `Nothing` (<xref:System.ArgumentNullException>).  
  
- Kullanıcının kayıt defteri anahtarlarını silme izinleri yoktur (<xref:System.Security.SecurityException>).  
  
- Anahtar adı 255 karakter sınırını aşıyor<xref:System.ArgumentException>( ).  
  
- Kayıt defteri anahtarı salt okunur<xref:System.UnauthorizedAccessException>( ).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Yeterli çalışma zamanı izinleri verilmezse veya<xref:System.Security.Permissions.RegistryPermission>kullanıcı ayarlar oluşturmak veya yazmak için doğru erişime (ALA'lar tarafından belirlendiği şekilde) sahip değilse kayıt defteri çağrıları başarısız olur. Örneğin, kod erişim güvenlik iznine sahip yerel bir uygulamanın işletim sistemi izni olmayabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [Güvenlik ve Kayıt Defteri](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
- [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
