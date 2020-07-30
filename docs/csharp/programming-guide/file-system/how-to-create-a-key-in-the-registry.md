---
title: Kayıt defteri-C# programlama kılavuzunda anahtar oluşturma
description: Kayıt defterinde anahtar oluşturmayı öğrenin. Bkz. bir kod örneği, yönergeleri derleme ve kullanılabilir ek kaynaklar.
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: 6db076bc22e098c285b74a8c10e8b5f456c2c55e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299987"
---
# <a name="how-to-create-a-key-in-the-registry-c-programming-guide"></a>Kayıt defterinde anahtar oluşturma (C# Programlama Kılavuzu)
Bu örnek, "ad" ve "Isabella" değer çiftini geçerli kullanıcının kayıt defterine, "adlar" anahtarı altında ekler.  
  
## <a name="example"></a>Örnek  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Kodu kopyalayın ve `Main` konsol uygulamasının yöntemine yapıştırın.  
  
- Parametresini, `Names` doğrudan kayıt defterinin HKEY_CURRENT_USER düğümünün altında bulunan bir anahtarın adıyla değiştirin.  
  
- `Name`Parametresini doğrudan Names düğümünün altında bulunan bir değerin adıyla değiştirin.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Anahtarınız için uygun bir konum bulmak üzere kayıt defteri yapısını inceleyin. Örneğin, geçerli kullanıcının yazılım anahtarını açmak ve şirketinizin adıyla bir anahtar oluşturmak isteyebilirsiniz. Ardından kayıt defteri değerlerini şirketinizin anahtarına ekleyin.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Anahtarın adı null.  
  
- Kullanıcının kayıt defteri anahtarları oluşturma izni yok.  
  
- Anahtar adı 255 karakterlik sınırı aşıyor.  
  
- Anahtar kapalıdır.  
  
- Kayıt defteri anahtarı salt okunurdur.  
  
## <a name="net-security"></a>.NET güvenliği  
 Yerel bilgisayar yerine, Kullanıcı klasörüne veri yazmak daha güvenlidir — `Microsoft.Win32.Registry.CurrentUser` `Microsoft.Win32.Registry.LocalMachine` .  
  
 Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa ne yapılacağını belirlemeniz gerekir. Belki de kötü amaçlı olan bir işlem, değeri zaten oluşturmuş ve ona erişime sahip olabilir. Verileri kayıt defteri değerine yerleştirdiğinizde, veriler diğer işlem tarafından kullanılabilir. Bunu engellemek için kullanın.`Overload:Microsoft.Win32.RegistryKey.GetValue` yöntemidir. Anahtar zaten mevcut değilse null değerini döndürür.  
  
 Kayıt defteri anahtarı erişim denetim listeleriyle (ACL) korunuyorsa bile, parolalar gibi gizli dizileri, kayıt defterinde düz metin olarak depolamak güvenli değildir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](./index.md)
- [C ile kayıt defterinden okuma, yazma ve silme #](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
