---
title: 'Nasıl yapılır: Ortak özel anahtar çifti oluşturma'
ms.date: 08/20/2019
helpviewer_keywords:
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 62c38494e29541bd490d69ccc8de485217b9514a
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991698"
---
# <a name="how-to-create-a-public-private-key-pair"></a>Nasıl yapılır: Ortak özel anahtar çifti oluşturma

Bir derlemeyi güçlü bir adla imzalamak için ortak/özel anahtar çiftiniz olmalıdır. Bu ortak ve özel şifreleme anahtarı çifti derleme sırasında, tanımlayıcı adlı bir derleme oluşturmak için kullanılır. [Tanımlayıcı ad Aracı (sn. exe)](../../framework/tools/sn-exe-strong-name-tool.md)kullanarak bir anahtar çifti oluşturabilirsiniz. Anahtar çifti dosyaları genellikle *. snk* uzantısına sahiptir.

> [!NOTE]
> Visual Studio 'da, C# ve Visual Basic proje özelliği sayfaları, var olan anahtar dosyaları seçmenize veya *sn. exe*' yi kullanmadan yeni anahtar dosyaları oluşturmanıza olanak sağlayan bir **imzalama** sekmesi içerir. Görsel C++' de, varolan bir anahtar dosyasının konumunu, **Özellik sayfaları** penceresinin **yapılandırma özellikleri** bölümünün **bağlayıcı** bölümünde bulunan **Gelişmiş** Özellik sayfasında belirtebilirsiniz. Anahtar dosya çiftlerini tanımlamak <xref:System.Reflection.AssemblyKeyFileAttribute> için özniteliğinin kullanımı, Visual Studio 2005 ' den itibaren artık kullanılmıyor olarak yapılmıştır.

## <a name="create-a-key-pair"></a>Anahtar çifti oluşturma

Bir anahtar çifti oluşturmak için, komut isteminde aşağıdaki komutu yazın:

**sn – k** \< *dosya adı*>

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

Bir derlemeyi tanımlayıcı bir adla imzalarken, [derleme Bağlayıcısı (al. exe)](../../framework/tools/al-exe-assembly-linker.md) , geçerli dizine ve çıkış dizinine göre anahtar dosyasını arar. Komut satırı derleyicileri kullanırken, anahtarı kod modüllerinizi içeren geçerli dizine kopyalamanız yeterlidir.

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
