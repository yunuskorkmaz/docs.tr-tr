---
title: "Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarını Silme"
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
ms.openlocfilehash: 8a983436b8c7415f0d356d65ae7d6c5ffd1c2db5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583857"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarını Silme
<xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> Ve <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> yöntemleri, kayıt defteri anahtarlarını silmeniz için kullanılabilir.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-delete-a-registry-key"></a>Bir kayıt defteri anahtarını silmek için  
  
-   Kullanım `DeleteSubKey` yöntemi bir kayıt defteri anahtarını silin. Bu örnek, yazılım/TestApp Currentuser'a kovanında anahtarı siler. Bu uygun dizeye kodda değişiklik ya da sahip kullanıcı tarafından sağlanan bilgileri kullanır.  
  
     [!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 `DeleteSubKey` Anahtar/değer çifti yoksa, yöntem boş bir dize döndürür.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Anahtar adı `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Kullanıcının kayıt defteri anahtarları silme izni yok (<xref:System.Security.SecurityException>).  
  
-   Anahtar adı 255 karakter sınırını aşıyor (<xref:System.ArgumentException>).  
  
-   Kayıt defteri anahtarı salt okunurdur (<xref:System.UnauthorizedAccessException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Kayıt defteri Çağrılar başarısız olur ya da yeterli çalıştırma izinleri olmayan verilirse (<xref:System.Security.Permissions.RegistryPermission>) veya kullanıcının ayarlarına oluşturulması veya doğru erişim (ACL'ler tarafından belirlendiği şekilde) yok. Örneğin, kod erişimi güvenlik izni olan yerel bir uygulama işletim sistemi izni olmayabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey>  
 [Güvenlik ve Kayıt Defteri](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
