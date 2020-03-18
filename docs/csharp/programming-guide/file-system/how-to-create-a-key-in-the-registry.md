---
title: Kayıt defterinde anahtar oluşturma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: 16974db950a3a460416cfb917147439707e1d007
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635450"
---
# <a name="how-to-create-a-key-in-the-registry-c-programming-guide"></a>Kayıt defterinde anahtar oluşturma (C# Programlama Kılavuzu)
Bu örnek, geçerli kullanıcının kayıt defterine "Adlar" anahtarı altında "Ad" ve "Isabella" değer çiftini ekler.  
  
## <a name="example"></a>Örnek  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Kodu kopyalayın ve konsol `Main` uygulamasının yöntemine yapıştırın.  
  
- Parametreyi, `Names` doğrudan kayıt defterinin HKEY_CURRENT_USER düğümünün altında bulunan bir anahtarın adı ile değiştirin.  
  
- Parametreyi, `Name` Doğrudan Ad düğümünün altında bulunan bir değerin adı ile değiştirin.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Anahtarınız için uygun bir yer bulmak için kayıt defteri yapısını inceleyin. Örneğin, geçerli kullanıcının Yazılım anahtarını açıp şirketinizin adını içeren bir anahtar oluşturmak isteyebilirsiniz. Ardından şirket defteri değerlerini şirketinizin anahtarına ekleyin.  
  
 Aşağıdaki koşullar bir özel durum neden olabilir:  
  
- Anahtarın adı geçersiz.  
  
- Kullanıcının kayıt defteri anahtarları oluşturma izinleri yoktur.  
  
- Anahtar adı 255 karakter sınırını aşıyor.  
  
- Anahtar kapalı.  
  
- Kayıt defteri anahtarı salt okunur.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Yerel bilgisayara değil, `Microsoft.Win32.Registry.CurrentUser` kullanıcı klasörüne veri yazmak daha güvenlidir. `Microsoft.Win32.Registry.LocalMachine`  
  
 Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa ne yapacağınız gerektiğine karar vermeniz gerekir. Başka bir işlem, belki de kötü niyetli bir, zaten değer yarattı ve ona erişimi olabilir. Verileri kayıt defteri değerine koyduğunuzda, veriler diğer işlem için kullanılabilir. Bunu önlemek için, kullanın.`Overload:Microsoft.Win32.RegistryKey.GetValue` Yöntem. Anahtar zaten yoksa null döndürür.  
  
 Kayıt defteri anahtarı erişim denetim listeleri (ACL) tarafından korunsa bile, parolalar gibi sırları kayıt defterinde düz metin olarak depolamak güvenli değildir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](./index.md)
- [C ile kayıt defterinden okuma, yazma ve silme #](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
