---
title: 'Nasıl Yapılır: Kayıt Defteri Anahtarından Değer Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: 73c32aefe06a68bb42fcb5f4615da0927e57e892
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345612"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarından Değer Okuma

`My.Computer.Registry` nesnesinin `GetValue` yöntemi Windows kayıt defterindeki değerleri okumak için kullanılabilir.  
  
 Aşağıdaki örnekteki "Software\MyApp" anahtarı yoksa, bir özel durum oluşturulur. `ValueName`, aşağıdaki örnekteki "Name" yoksa, `Nothing` döndürülür.  
  
 `GetValue` yöntemi, belirli bir değerin belirli bir kayıt defteri anahtarında bulunup bulunmadığını anlamak için de kullanılabilir.  
  
 Kod, bir Web uygulamasından kayıt defterini okuduğunda, geçerli kullanıcı Web uygulamasında uygulanan kimlik doğrulama ve kimliğe bürünme tarafından belirlenir.  
  
### <a name="to-read-a-value-from-a-registry-key"></a>Kayıt defteri anahtarından bir değeri okumak için  
  
- Kayıt defteri anahtarından bir değeri okumak için yolu ve adı belirterek `GetValue` yöntemi kullanın. Aşağıdaki örnek `Name` değeri `HKEY_CURRENT_USER\Software\MyApp` okur ve bir ileti kutusunda görüntüler.  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **Windows Işletim sistemi > kayıt defterinde**bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>Bir kayıt defteri anahtarında bir değerin bulunup bulunmadığını belirleme  
  
- Değeri almak için `GetValue` yöntemini kullanın. Aşağıdaki kod değerin mevcut olup olmadığını denetler ve yoksa bir ileti döndürür.  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Kayıt defteri, verileri depolamak için kullanılan en üst düzey veya kök anahtarlar içerir. Örneğin, HKEY_LOCAL_MACHINE kök anahtarı, tüm kullanıcılar tarafından kullanılan makine düzeyindeki ayarları depolamak için kullanılır, HKEY_CURRENT_USER tek bir kullanıcıya özgü verileri depolamak için kullanılır.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Anahtarın adı `Nothing` (<xref:System.ArgumentNullException>).  
  
- Kullanıcının kayıt defteri anahtarlarından okuma izni yok (<xref:System.Security.SecurityException>).  
  
- Anahtar adı 255 karakterlik sınırı (<xref:System.ArgumentException>) aşıyor.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Bu işlemi çalıştırmak için, derlemeniz <xref:System.Security.Permissions.RegistryPermission> sınıfı tarafından verilen ayrıcalık düzeyini gerektirir. Kısmi güven bağlamında çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum oluşturabilir. Benzer şekilde, Kullanıcı oluşturma veya ayarları yazma için doğru ACL 'Lere sahip olmalıdır. Örneğin, kod erişim güvenliği iznine sahip bir yerel uygulama işletim sistemi iznine sahip olmayabilir. Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
