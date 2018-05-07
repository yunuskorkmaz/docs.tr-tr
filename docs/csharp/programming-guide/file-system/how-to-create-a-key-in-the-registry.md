---
title: 'Nasıl yapılır: Kayıt Defterinde Anahtar Oluşturma (Visual C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: a1643310740a472ad0a1df978fa41f674f3dbcb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a>Nasıl yapılır: Kayıt Defterinde Anahtar Oluşturma (Visual C#)
Bu örnek, geçerli kullanıcının kayıt defteri anahtarı "Adı" altında "Name" ve "Isabella" değer çifti ekler.  
  
## <a name="example"></a>Örnek  
  
```  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Kodu kopyalayın ve yapıştırın `Main` bir konsol uygulaması yöntemi.  
  
-   Değiştir `Names` doğrudan kayıt defterinin HKEY_CURRENT_USER düğümünde mevcut bir anahtarı adlı parametre.  
  
-   Değiştir `Name` doğrudan adları düğümü altında varolan bir değer adlı parametre.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Anahtarınız için uygun bir konum bulmak için kayıt defteri yapısı inceleyin. Örneğin, geçerli kullanıcının yazılım anahtarı açın ve şirketinizin adı ile bir anahtar oluşturmak isteyebilirsiniz. Ardından, şirketinizin anahtarına kayıt defteri değerlerini ekleyin.  
  
 Aşağıdaki koşullar, bir özel durum neden olabilir:  
  
-   Anahtar adı null.  
  
-   Kullanıcının kayıt defteri anahtarları oluşturma izni yok.  
  
-   Anahtar adı 255 karakter sınırını aşıyor.  
  
-   Anahtar kapalı.  
  
-   Kayıt defteri anahtarı salt okunurdur.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Kullanıcı klasörüne veri yazmak için daha güvenlidir — `Microsoft.Win32.Registry.CurrentUser` — yerine yerel bilgisayarda — `Microsoft.Win32.Registry.LocalMachine`.  
  
 Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa yapmanız gerekenler karar vermeniz gerekir. Başka bir işlem, belki de kötü amaçlı bir değer önceden oluşturduğunuz ve buna erişiminiz. Kayıt defteri değerindeki veri geçirdiğinizde, verileri başka bir işlem mevcut değil. Bunu önlemek için kullanın.`Overload:Microsoft.Win32.RegistryKey.GetValue` yöntem. Anahtar zaten mevcut değilse null değerini döndürür.  
  
 Kayıt defteri anahtarı erişim denetim listeleri (ACL) tarafından korunan olsa bile düz metin olarak kayıt defterinde parolalar gibi gizli depolamak için güvenli değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO?displayProperty=nameWithType>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](../../../csharp/programming-guide/file-system/index.md)  
 [Okuma, yazma ve C# ile kayıt defterinden silme](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
