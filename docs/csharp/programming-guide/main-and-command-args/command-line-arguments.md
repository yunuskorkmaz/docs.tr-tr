---
title: Komut satırı bağımsız değişkenleri- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: d6775263e6f1afb227aa263b01d60f5181da74f3
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093516"
---
# <a name="command-line-arguments-c-programming-guide"></a>Komut Satırı Bağımsız Değişkenleri (C# Programlama Kılavuzu)

Aşağıdaki yöntemlerden biriyle yöntemi tanımlayarak `Main` metoduna bağımsız değişkenler gönderebilirsiniz:

[!code-csharp[csProgGuideMain#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#2)]  

[!code-csharp[csProgGuideMain#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#3)]

> [!NOTE]
> Windows Forms uygulamasındaki `Main` yönteminde komut satırı bağımsız değişkenlerini etkinleştirmek için, *program.cs*içinde `Main` imzasını el ile değiştirmeniz gerekir. Windows Forms Tasarımcısı tarafından oluşturulan kod, giriş parametresi olmadan bir `Main` oluşturur. Ayrıca, bir konsolun veya Windows uygulamasındaki herhangi bir noktadan komut satırı bağımsız değişkenlerine erişmek için <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> veya <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> kullanabilirsiniz.

`Main` yönteminin parametresi, komut satırı bağımsız değişkenlerini temsil eden bir <xref:System.String> dizisidir. Genellikle `Length` özelliğini test ederek bağımsız değişkenlerin mevcut olup olmadığını belirlersiniz, örneğin:

[!code-csharp[csProgGuideMain#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#4)]

Ayrıca, <xref:System.Convert> sınıfını veya `Parse` yöntemini kullanarak dize bağımsız değişkenlerini sayısal türlere dönüştürebilirsiniz. Örneğin, aşağıdaki ifade <xref:System.Int64.Parse%2A> yöntemini kullanarak `string` bir `long` numarasına dönüştürür:

```csharp
long num = Int64.Parse(args[0]);
```

Ayrıca, `Int64`diğer ad `long`C# türü kullanmak da mümkündür:

```csharp
long num = long.Parse(args[0]);
```

Aynı şeyi yapmak için `ToInt64` `Convert` sınıf yöntemini de kullanabilirsiniz:

```csharp
long num = Convert.ToInt64(s);
```

Daha fazla bilgi için bkz. <xref:System.Int64.Parse%2A> ve <xref:System.Convert>.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir konsol uygulamasında komut satırı bağımsız değişkenlerinin nasıl kullanılacağını gösterir. Uygulama çalışma zamanında bir bağımsız değişken alır, bağımsız değişkeni bir tamsayıya dönüştürür ve sayının faktöriyelini hesaplar. Bağımsız değişken sağlanmazsa, uygulama programın doğru kullanımını açıklayan bir ileti yayınlar.

Uygulamayı bir komut isteminden derlemek ve çalıştırmak için aşağıdaki adımları izleyin:

1. Aşağıdaki kodu herhangi bir metin düzenleyicisine yapıştırın ve sonra dosyayı *Factorial.cs*adlı bir metin dosyası olarak kaydedin.

     [!code-csharp[csProgGuideMain#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#16)]

2. **Başlat** ekranından veya **Başlat** menüsünden bir Visual Studio **Geliştirici komut istemi** penceresi açın ve ardından yeni oluşturduğunuz dosyayı içeren klasöre gidin.

3. Uygulamayı derlemek için aşağıdaki komutu girin.
  
     `csc Factorial.cs`  
  
     Uygulamanızda hiçbir derleme hatası yoksa, *çarpınımı. exe* adlı bir yürütülebilir dosya oluşturulur.
  
4. 3 ' ün çarpımını hesaplamak için aşağıdaki komutu girin:
  
     `Factorial 3`  
  
5. Komut bu çıktıyı üretir: `The factorial of 3 is 6.`

> [!NOTE]
> Visual Studio 'da bir uygulama çalıştırırken, [hata ayıklama sayfasında, proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer)' nda komut satırı bağımsız değişkenlerini belirtebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Environment?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](index.md)
- [Komut satırı bağımsız değişkenlerini görüntüleme](how-to-display-command-line-arguments.md)
- [Ana() Dönüş Değerleri](main-return-values.md)
- [Sınıflar](../classes-and-structs/classes.md)
