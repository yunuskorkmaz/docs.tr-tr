---
title: 'Nasıl yapılır: Kayıt Defteri Anahtarından Değer Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: 74069b111f4316eb81c74f5e62c1fbff6ab8f4b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401855"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarından Değer Okuma

`GetValue`Nesne yöntemi, `My.Computer.Registry` Windows kayıt defterindeki değerleri okumak için kullanılabilir.  
  
 Aşağıdaki örnekteki "Software\MyApp" anahtarı yoksa, bir özel durum oluşturulur. , `ValueName` Aşağıdaki örnekteki "Name" mevcut değilse, `Nothing` döndürülür.  
  
 `GetValue`Yöntemi, belirli bir değerin belirli bir kayıt defteri anahtarında bulunup bulunmadığını anlamak için de kullanılabilir.  
  
 Kod, bir Web uygulamasından kayıt defterini okuduğunda, geçerli kullanıcı Web uygulamasında uygulanan kimlik doğrulama ve kimliğe bürünme tarafından belirlenir.  
  
### <a name="to-read-a-value-from-a-registry-key"></a>Kayıt defteri anahtarından bir değeri okumak için  
  
- `GetValue`Kayıt defteri anahtarından bir değeri okumak için yolu ve adı belirterek yöntemi kullanın. Aşağıdaki örnek, öğesinden değerini okur `Name` `HKEY_CURRENT_USER\Software\MyApp` ve bir ileti kutusunda görüntüler.  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **Windows Işletim sistemi > kayıt defterinde**bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>Bir kayıt defteri anahtarında bir değerin bulunup bulunmadığını belirleme  
  
- `GetValue`Değerini almak için yöntemini kullanın. Aşağıdaki kod değerin mevcut olup olmadığını denetler ve yoksa bir ileti döndürür.  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Kayıt defteri, verileri depolamak için kullanılan en üst düzey veya kök anahtarlar içerir. Örneğin, HKEY_LOCAL_MACHINE kök anahtarı, tüm kullanıcılar tarafından kullanılan makine düzeyindeki ayarları depolamak için kullanılır, HKEY_CURRENT_USER tek bir kullanıcıya özgü verileri depolamak için kullanılır.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Anahtarın adı `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- Kullanıcının kayıt defteri anahtarlarından okuma izni yok ( <xref:System.Security.SecurityException> ).  
  
- Anahtar adı 255 karakter sınırını ( <xref:System.ArgumentException> ) aşıyor.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Bu işlemi çalıştırmak için, derlemeniz sınıf tarafından verilen bir ayrıcalık düzeyi gerektiriyor <xref:System.Security.Permissions.RegistryPermission> . Kısmi güven bağlamında çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum oluşturabilir. Benzer şekilde, Kullanıcı oluşturma veya ayarları yazma için doğru ACL 'Lere sahip olmalıdır. Örneğin, kod erişim güvenliği iznine sahip bir yerel uygulama işletim sistemi iznine sahip olmayabilir. Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](reading-from-and-writing-to-the-registry.md)
