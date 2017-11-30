---
title: "Nasıl yapılır: Kayıt Defterinde Anahtar Oluşturma (Visual C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6cc79a8a914d3ef5b7c496db4dc0d2b3eb17768
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](../../../csharp/programming-guide/file-system/index.md)  
 [Okuma, yazma ve C# ile kayıt defterinden silme](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
