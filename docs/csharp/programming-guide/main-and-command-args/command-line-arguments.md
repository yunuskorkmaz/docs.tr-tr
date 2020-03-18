---
title: Komut Satırı Bağımsız Değişkenleri - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: d6775263e6f1afb227aa263b01d60f5181da74f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093516"
---
# <a name="command-line-arguments-c-programming-guide"></a>Komut Satırı Bağımsız Değişkenleri (C# Programlama Kılavuzu)

Yöntemi aşağıdaki yollardan `Main` biriyle tanımlayarak bağımsız değişkenleri yönteme gönderebilirsiniz:

[!code-csharp[csProgGuideMain#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#2)]  

[!code-csharp[csProgGuideMain#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#3)]

> [!NOTE]
> Windows Forms uygulamasındayöntemdeki `Main` komut satırı bağımsız değişkenlerini etkinleştirmek `Main` *için, program.cs'daki*imzayı el ile değiştirmeniz gerekir. Windows Forms tasarımcısı tarafından oluşturulan kod, giriş parametresi olmadan bir `Main` gelir oluşturur. Konsol veya <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> Windows uygulamasındaki herhangi bir noktadan komut satırı bağımsız değişkenlerini de kullanabilir veya bunları erişebilirsiniz.

`Main` Yöntemin parametresi komut <xref:System.String> satırı bağımsız değişkenlerini temsil eden bir dizidir. Genellikle bağımsız değişkenlerin `Length` özelliği sınayarak var olup olmadığını belirlersiniz, örneğin:

[!code-csharp[csProgGuideMain#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#4)]

<xref:System.Convert> Ayrıca, sınıfı veya yöntemi kullanarak dize bağımsız değişkenlerini `Parse` sayısal türlere dönüştürebilirsiniz. Örneğin, aşağıdaki deyim `string` `long` <xref:System.Int64.Parse%2A> yöntemi kullanarak bir sayıya dönüştürür:

```csharp
long num = Int64.Parse(args[0]);
```

C# türünü `long`de kullanmak mümkündür, hangi `Int64`diğer adlar:

```csharp
long num = long.Parse(args[0]);
```

Aynı şeyi yapmak `Convert` için `ToInt64` sınıf yöntemini de kullanabilirsiniz:

```csharp
long num = Convert.ToInt64(s);
```

Daha fazla bilgi için <xref:System.Int64.Parse%2A> ve <xref:System.Convert> bölümlerine bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, konsol uygulamasında komut satırı bağımsız değişkenleri nasıl kullanılacağı gösterilmektedir. Uygulama çalışma zamanında bir bağımsız değişken alır, bağımsız değişkeni bir arayine dönüştürür ve sayının faktöriyelini hesaplar. Bağımsız değişken sağlanmazsa, uygulama programın doğru kullanımını açıklayan bir ileti yayınlar.

Uygulamayı bir komut isteminden derlemek ve çalıştırmak için aşağıdaki adımları izleyin:

1. Aşağıdaki kodu herhangi bir metin düzenleyicisine yapıştırın ve ardından dosyayı *Factorial.cs*adıyla bir metin dosyası olarak kaydedin.

     [!code-csharp[csProgGuideMain#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#16)]

2. **Başlangıç** ekranından veya **Başlat** menüsünden, Visual Studio Developer **Command Prompt** penceresini açın ve ardından az önce oluşturduğunuz dosyayı içeren klasöre gidin.

3. Uygulamayı derlemek için aşağıdaki komutu girin.
  
     `csc Factorial.cs`  
  
     Uygulamanızda derleme hatası yoksa, *Factorial.exe* adında bir yürütülebilir dosya oluşturulur.
  
4. 3 faktöriyel hesaplamak için aşağıdaki komutu girin:
  
     `Factorial 3`  
  
5. Komut bu çıktıyı üretir:`The factorial of 3 is 6.`

> [!NOTE]
> Visual Studio'da bir uygulama çalıştırırken Hata [Ayıklama Sayfasında, Proje Tasarımcısı'nda](/visualstudio/ide/reference/debug-page-project-designer)komut satırı bağımsız değişkenlerini belirtebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Environment?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](index.md)
- [Komut satırı bağımsız değişkenleri nasıl görüntülenir?](how-to-display-command-line-arguments.md)
- [Ana() Dönüş Değerleri](main-return-values.md)
- [Sınıflar](../classes-and-structs/classes.md)
