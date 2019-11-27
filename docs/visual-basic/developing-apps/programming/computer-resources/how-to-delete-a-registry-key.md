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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345647"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarını Silme

<xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> ve <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> yöntemleri kayıt defteri anahtarlarını silmek için kullanılabilir.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-delete-a-registry-key"></a>Kayıt defteri anahtarını silmek için  
  
- Bir kayıt defteri anahtarını silmek için `DeleteSubKey` yöntemini kullanın. Bu örnek, geçerli kullanıcı kovanındaki Key Software/TestApp öğesini siler. Bu kodu kodda uygun dizeye değiştirebilir veya Kullanıcı tarafından sağlanan bilgileri kullanabilir.  
  
     [!code-vb[VbResourceTasks#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Anahtar/değer çifti yoksa `DeleteSubKey` yöntemi boş bir dize döndürür.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Anahtarın adı `Nothing` (<xref:System.ArgumentNullException>).  
  
- Kullanıcının kayıt defteri anahtarlarını silme izni yok (<xref:System.Security.SecurityException>).  
  
- Anahtar adı 255 karakterlik sınırı (<xref:System.ArgumentException>) aşıyor.  
  
- Kayıt defteri anahtarı salt okunurdur (<xref:System.UnauthorizedAccessException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Yeterli çalışma zamanı izni verilmezse (<xref:System.Security.Permissions.RegistryPermission>) veya Kullanıcı, ayarları oluşturmaya veya bu ayarlara yazmaya yönelik doğru erişime (ACL 'Ler tarafından belirlendiği şekilde) sahip değilse, kayıt defteri çağrıları başarısız olur. Örneğin, kod erişim güvenliği iznine sahip bir yerel uygulama işletim sistemi iznine sahip olmayabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [Güvenlik ve Kayıt Defteri](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
- [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
