---
title: 'Nasıl yapılır: genel-özel anahtar çifti oluşturma'
description: Derleme sırasında kullanılmak üzere tanımlayıcı adlı bir derleme oluşturmak için ortak/özel bir şifreleme anahtarı çifti oluşturmayı öğrenin.
ms.date: 08/20/2019
helpviewer_keywords:
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: c42e98a7e27ded9a21445fae35ade843e834076a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163499"
---
# <a name="how-to-create-a-public-private-key-pair"></a>Nasıl yapılır: genel-özel anahtar çifti oluşturma

Bir derlemeyi güçlü bir adla imzalamak için ortak/özel anahtar çiftiniz olmalıdır. Bu ortak ve özel şifreleme anahtarı çifti derleme sırasında, tanımlayıcı adlı bir derleme oluşturmak için kullanılır. [Tanımlayıcı ad aracını (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md)kullanarak bir anahtar çifti oluşturabilirsiniz. Anahtar çifti dosyaları genellikle *. snk* uzantısına sahiptir.

> [!NOTE]
> Visual Studio 'da C# ve Visual Basic proje özellik sayfaları, var olan anahtar dosyaları seçmenize veya *Sn.exe*kullanmadan yeni anahtar dosyaları oluşturmanıza olanak sağlayan bir **imzalama** sekmesi içerir. Visual C++, var olan bir anahtar dosyasının konumunu, **Özellik sayfaları** penceresinin **yapılandırma özellikleri** bölümünün **bağlayıcı** bölümünde bulunan **Gelişmiş** Özellik sayfasında belirtebilirsiniz. <xref:System.Reflection.AssemblyKeyFileAttribute>Anahtar dosya çiftlerini tanımlamak için özniteliğinin kullanımı, Visual Studio 2005 ' den itibaren artık kullanılmıyor olarak yapılmıştır.

## <a name="create-a-key-pair"></a>Anahtar çifti oluşturma

Bir anahtar çifti oluşturmak için, komut isteminde aşağıdaki komutu yazın:

**sn – k**\<*file name*>

Bu komutta *dosya adı* , anahtar çiftini içeren çıkış dosyasının adıdır.

Aşağıdaki örnek, *sgKey. snk*adlı bir anahtar çifti oluşturur.

```cmd
sn -k sgKey.snk
```

Bir derlemeyi imzalamayı ve tüm anahtar çiftini (test senaryolarından çok önemli olmayan) denetlemeniz gerekiyorsa, bir anahtar çifti oluşturmak için aşağıdaki komutları kullanabilir ve sonra ortak anahtarı ayrı bir dosyaya ayıklayabilirsiniz. İlk olarak, anahtar çiftini oluşturun:

```cmd
sn -k keypair.snk
```

Sonra, ortak anahtarı anahtar çiftinden ayıklayın ve ayrı bir dosyaya kopyalayın:

```cmd
sn -p keypair.snk public.snk
```

Anahtar çiftini oluşturduktan sonra, tanımlayıcı ad imzalama araçlarının bulabileceği dosyayı yerleştirmeniz gerekir.

Bir derlemeyi tanımlayıcı bir adla imzalarken, [derleme Bağlayıcısı (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) geçerli dizine ve çıkış dizinine göre anahtar dosyasını arar. Komut satırı derleyicileri kullanırken, anahtarı kod modüllerinizi içeren geçerli dizine kopyalamanız yeterlidir.

Visual Studio 'nun proje özelliklerinde **imzalama** sekmesi olmayan önceki bir sürümünü kullanıyorsanız, önerilen anahtar dosyası konumu aşağıdaki şekilde belirtilen dosya özniteliğine sahip proje dizinidir:

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcı adlı derlemeler oluşturma ve kullanma](create-use-strong-named.md)
