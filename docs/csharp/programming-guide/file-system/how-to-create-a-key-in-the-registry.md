---
title: 'Nasıl yapılır: Kayıt Defterinde Anahtar Oluşturma (Visual C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: f2b2cfcb09dc0c8c4d65b64f5de55c0b72746457
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480614"
---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a>Nasıl yapılır: Kayıt Defterinde Anahtar Oluşturma (Visual C#)
Bu örnek "Name" ve "Isabella" değer çiftini geçerli kullanıcının kayıt defterine "Names" anahtarı altına ekler.  
  
## <a name="example"></a>Örnek  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Kodu kopyalayın ve yapıştırın `Main` konsol uygulamasının yöntemi.  
  
-   Değiştirin `Names` parametresini doğrudan kayıt defterinin HKEY_CURRENT_USER düğümünde bulunan bir anahtarın adıyla.  
  
-   Değiştirin `Name` parametresini doğrudan adlar düğümünde bulunan bir değerin adıyla.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Anahtarınız için uygun bir konum bulmak üzere kayıt yapısını inceleyin. Örneğin, geçerli kullanıcı için yazılım anahtarını açmak ve şirketinizin adıyla bir anahtar oluşturmak isteyebilirsiniz. Ardından kayıt defteri değerlerini şirketinizin anahtarına ekleyin.  
  
 Aşağıdaki koşullar özel bir duruma neden:  
  
-   Anahtar adı null.  
  
-   Kullanıcının kayıt defteri anahtarlarını oluşturma izni yok.  
  
-   Anahtar adı 255 karakter sınırını aşıyor.  
  
-   Anahtar kapalı.  
  
-   Kayıt defteri anahtarı salt okunurdur.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Verilerin kullanıcı klasörüne yazılması daha güvenlidir; `Microsoft.Win32.Registry.CurrentUser` — yerine yerel bilgisayarda — `Microsoft.Win32.Registry.LocalMachine`.  
  
 Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa yapmanız gerekenler karar vermeniz gerekir. Başka bir işlem, belki de kötü amaçlı bir değeri önceden oluşturmuş olabilir ve erişmesini sağlayabilirsiniz. Kayıt defteri değerine veri koyduğunuzda, veriler başka bir işlem için kullanılabilir. Bunu önlemek için kullanın.`Overload:Microsoft.Win32.RegistryKey.GetValue` yöntem. Anahtar zaten mevcut değilse null değerini döndürür.  
  
 Kayıt defteri anahtarı erişim denetim listeleri (ACL) korunuyor olsa bile kayıt defterinde düz metin parolalar gibi gizli dizileri depolamak için güvenli değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO?displayProperty=nameWithType>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](../../../csharp/programming-guide/file-system/index.md)  
 [Okuma, yazma ve C# ile kayıt silme](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
