---
title: Üst düzey deyimler-C# Programlama Kılavuzu
description: C# 9 ve sonraki sürümlerinde en üst düzey deyimler hakkında bilgi edinin.
ms.date: 03/08/2021
helpviewer_keywords:
- C# language, top-level statements
- C# language, Main method
ms.openlocfilehash: 69ff5fd606f5e12f55bd3e6dfc15fc7e64d8352b
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190477"
---
# <a name="top-level-statements-c-programming-guide"></a>Üst düzey deyimler (C# Programlama Kılavuzu)

C# 9 ' dan itibaren bir `Main` konsol uygulaması projesine bir yöntemi açıkça eklemeniz gerekmez. Bunun yerine, *en üst düzey deyimler* özelliğini kullanarak yazmanız gerektiğini kodun en aza indirmenize olanak sağlayabilirsiniz. Bu durumda, derleyici uygulama için bir sınıf ve `Main` Yöntem giriş noktası oluşturur.

C# 9 ' da bir bütün C# programı olan bir *program.cs* dosyası aşağıda verilmiştir:

:::code language="csharp" source="snippets/top-level-statements-1/Program.cs":::

Üst düzey deyimler, Azure Işlevleri ve GitHub eylemleri gibi küçük yardımcı programlara yönelik basit programlar yazmanızı sağlar. Ayrıca, yeni C# programcıları için kod öğrenmeye ve yazmaya başlamanıza da daha kolay hale gelir.

Aşağıdaki bölümlerde, en üst düzey deyimlerle yapabilecekleriniz ve yapabileceklerinize ilişkin kurallar açıklanmaktadır.

## <a name="only-one-top-level-file"></a>Yalnızca bir üst düzey dosya

Bir uygulamanın yalnızca bir giriş noktası olması gerekir, bu nedenle bir projede en üst düzey deyimlerle yalnızca bir dosya olabilir. En üst düzey deyimleri bir projede birden fazla dosyaya koymak aşağıdaki derleyici hatasına neden olur:

> CS8802 yalnızca bir derleme birimi en üst düzey deyimlerine sahip olabilir.

Bir proje, en üst düzey deyimleri olmayan herhangi bir sayıda ek kaynak kodu dosyasına sahip olabilir.

## <a name="no-other-entry-points"></a>Başka giriş noktası yok

Bir `Main` yöntemi açıkça yazabilirsiniz, ancak giriş noktası olarak çalışamaz. Derleyici aşağıdaki uyarıyı verir:

> CS7022, programın giriş noktası genel koddur; ' Main () ' giriş noktası yoksayılıyor.

Üst düzey deyimler içeren bir projede, proje bir veya daha fazla yöntem içerse bile, giriş noktasını seçmek için [-Main](../../language-reference/compiler-options/main-compiler-option.md) derleyici seçeneğini kullanamazsınız `Main` .

## <a name="using-directives"></a>`using` yönergeler

Using yönergelerini eklerseniz, bu örnekte olduğu gibi, ilk olarak dosyada gelmelidir:

:::code language="csharp" source="snippets/top-level-statements-1/Program.cs":::

## <a name="global-namespace"></a>Genel ad alanı

En üst düzey deyimler, genel ad alanında örtülü olarak bulunur.

## <a name="namespaces-and-type-definitions"></a>Ad alanları ve tür tanımları

En üst düzey deyimlerle bir dosya ad alanları ve tür tanımları da içerebilir, ancak en üst düzey deyimlerden sonra gelmesi gerekir. Örnek:

:::code language="csharp" source="snippets/top-level-statements-2/Program.cs":::

## `args`

En üst düzey deyimler, `args` girilen tüm komut satırı bağımsız değişkenlerine erişmek için değişkenine başvurabilir. `args`Değişken hiçbir şekilde null değildir ancak `Length` hiçbir komut satırı bağımsız değişkeni sağlanmazsa sıfır olur. Örnek:

:::code language="csharp" source="snippets/top-level-statements-3/Program.cs":::

## `await`

Kullanarak zaman uyumsuz bir yöntem çağırabilirsiniz `await` . Örnek:

:::code language="csharp" source="snippets/top-level-statements-4/Program.cs":::

## <a name="exit-code-for-the-process"></a>İşlem için çıkış kodu

`int`Uygulama sona erdiğinde bir değer döndürmek için, `return` ifadesini döndüren bir yöntemde olduğu gibi kullanın `Main` `int` . Örnek:

:::code language="csharp" source="snippets/top-level-statements-5/Program.cs":::

## <a name="implicit-entry-point-method"></a>Örtük giriş noktası yöntemi

Derleyici, en üst düzey deyimlerle bir proje için program giriş noktası olarak kullanılacak bir yöntem oluşturur. Bu yöntemin adı aslında değil `Main` , kodunuzun doğrudan başvurılemeyeceğini bir uygulama ayrıntısı. Yönteminin imzası, en üst düzey deyimlerin anahtar sözcüğünü mi yoksa deyimini mi içerdiğini bağlıdır `await` `return` . Aşağıdaki tabloda, yöntemi için tablodaki Yöntem adı kullanılarak yöntem imzasının nasıl görünebilecekleri gösterilmektedir `Main` .

| Üst düzey kod içerir| Örtük `Main` imza                    |
|------------------------|----------------------------------------------|
| `await` ve `return`   | `static async Task<int> Main(string[] args)` |
| `await`                | `static async Task Main(string[] args)`      |
| `return`               | `static int Main(string[] args)`             |
| Hayır `await` veya `return` | `static void Main(string[] args)`            |

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
[Üst düzey deyimler](~/_csharplang/proposals/csharp-9.0/top-level-statements.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Yöntemler](../classes-and-structs/methods.md)
- [C# programı içinde](../inside-a-program/index.md)
