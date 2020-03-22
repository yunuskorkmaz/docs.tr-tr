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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345612"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarından Değer Okuma

`My.Computer.Registry` Nesnenin `GetValue` yöntemi, Windows kayıt defterindeki değerleri okumak için kullanılabilir.  
  
 Aşağıdaki örnekte yer alan "Software\MyApp" tuşu yoksa bir özel durum atılır. Aşağıdaki `ValueName`örnekte "Ad" yoksa, `Nothing` döndürülür.  
  
 Yöntem, `GetValue` belirli bir kayıt defteri anahtarında belirli bir değerin bulunup bulunmadığını belirlemek için de kullanılabilir.  
  
 Kod bir Web uygulamasından kayıt defterini okuduğunda, geçerli kullanıcı Web uygulamasında uygulanan kimlik doğrulama ve kimliğe bürünme tarafından belirlenir.  
  
### <a name="to-read-a-value-from-a-registry-key"></a>Kayıt defteri anahtarından bir değeri okumak için  
  
- Kayıt `GetValue` defteri anahtarından bir değer okumak için yolu ve adı belirterek yöntemi kullanın. Aşağıdaki örnekteki değeri `Name` `HKEY_CURRENT_USER\Software\MyApp` okur ve bir ileti kutusunda görüntüler.  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 Bu kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir. Kod snippet picker, **Windows İşletim Sistemi > Kayıt Bulunmaktadır.** Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a>Kayıt defteri anahtarında bir değerin bulunup bulunmadığını belirlemek için  
  
- Değeri `GetValue` almak için yöntemi kullanın. Aşağıdaki kod, değerin var olup olmadığını denetler ve yoksa bir iletiyi döndürür.  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Kayıt defteri, verileri depolamak için kullanılan üst düzey veya kök anahtarlarını tutar. Örneğin, HKEY_LOCAL_MACHINE kök anahtarı tüm kullanıcılar tarafından kullanılan makine düzeyindeayarları depolamak için kullanılırken, HKEY_CURRENT_USER tek bir kullanıcıya özgü verileri depolamak için kullanılır.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Anahtarın adı `Nothing` (<xref:System.ArgumentNullException>).  
  
- Kullanıcının kayıt defteri anahtarlarından okuma izni<xref:System.Security.SecurityException>yoktur ( ).  
  
- Anahtar adı 255 karakter sınırını aşıyor<xref:System.ArgumentException>( ).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Bu işlemi çalıştırmak için derlemeniz <xref:System.Security.Permissions.RegistryPermission> sınıf tarafından verilen bir ayrıcalık düzeyi gerektirir. Kısmi güven bağlamında çalışıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum atabilir. Benzer şekilde, kullanıcının ayarlar oluşturmak veya yazmak için doğru ALA'lara sahip olması gerekir. Örneğin, kod erişim güvenlik iznine sahip yerel bir uygulamanın işletim sistemi izni olmayabilir. Daha fazla bilgi için [Kod Erişim Güvenlik Temelleri'ne](../../../../framework/misc/code-access-security-basics.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
