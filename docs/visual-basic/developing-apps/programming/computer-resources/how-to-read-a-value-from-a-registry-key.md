---
title: "Nasıl yapılır: Visual Basic'te kayıt defteri anahtarından değer okuma"
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: bc71dd2e3a78454236b2f6f30c2d51aa596e5b8c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840191"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te kayıt defteri anahtarından değer okuma
`GetValue` Yöntemi `My.Computer.Registry` nesne, Windows kayıt defteri değerlerini okumak için kullanılabilir.  
  
 Aşağıdaki örnekte, "Software\MyApp" anahtar mevcut değilse bir özel durum oluşturulur. Varsa `ValueName`, "Name" aşağıdaki örnekte, mevcut değil, `Nothing` döndürülür.  
  
 `GetValue` Yöntemi de belirli bir değeri belirli kayıt defteri anahtarında var olup olmadığını belirlemek için kullanılabilir.  
  
 Kodu bir Web uygulamasından kayıt defteri okuduğunda, geçerli kullanıcının kimlik doğrulaması ve Web uygulamasında gerçekleştirilen kimliğe bürünme tarafından belirlenir.  
  
### <a name="to-read-a-value-from-a-registry-key"></a>Kayıt defteri anahtarından değer okuma için  
  
-   Kullanma `GetValue` yolunu ve adını belirterek yöntemi) kayıt defteri anahtarından değer okuma için. Aşağıdaki örnek değeri okuyan `Name` gelen `HKEY_CURRENT_USER\Software\MyApp` ve bir ileti kutusunda görüntüler.  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici'de bulunur **Windows işletim sistemi > kayıt defteri**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>Bir değer olup olmadığını belirlemek için bir kayıt defteri anahtarında var.  
  
-   Kullanım `GetValue` değerini almak için yöntemi. Aşağıdaki kod, değeri var ve bir ileti döndürür, aksi takdirde denetler.  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Kayıt defteri, üst düzey tutan veya kök, verileri depolamak için kullanılan anahtarları. Örneğin, HKEY_LOCAL_MACHINE kök anahtarı kullanılırken HKEY_CURRENT_USER tek bir kullanıcıya özgü verileri depolamak için tüm kullanıcılar tarafından kullanılan makine düzeyinde ayarlarını depolamak için kullanılır.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Anahtar adı `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Kullanıcı kayıt defteri anahtarlarını Okuma izinlerine sahip değil (<xref:System.Security.SecurityException>).  
  
-   Anahtar adı 255 karakter sınırını aşıyor (<xref:System.ArgumentException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu işlemi çalıştırmak için ayrıcalık düzeyi verilen tarafından derlemeyi <xref:System.Security.Permissions.RegistryPermission> sınıfı. Kısmi güven bağlamda çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum fırlatabilir. Benzer şekilde, kullanıcı oluşturma veya ayarlarına yazma için doğru ACL'leri olması gerekir. Örneğin, kod erişim güvenlik izni olan yerel bir uygulama işletim sistemi izniniz olmayabilir. Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
