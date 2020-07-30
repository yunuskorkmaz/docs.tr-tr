---
title: Komut satırı bağımsız değişkenleri-C# Programlama Kılavuzu
description: Komut satırı bağımsız değişkenleri hakkında bilgi edinin. Konsol uygulamasında komut satırı bağımsız değişkenlerini kullanan bir örneğe bakın.
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: 35ff0425d3f09cf4ad116cf688b943cef3ef02e3
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381924"
---
# <a name="command-line-arguments-c-programming-guide"></a>Komut Satırı Bağımsız Değişkenleri (C# Programlama Kılavuzu)

Yöntemi `Main` aşağıdaki yöntemlerden biriyle tanımlayarak yöntemine bağımsız değişkenler gönderebilirsiniz:

[!code-csharp[csProgGuideMain#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#2)]  

[!code-csharp[csProgGuideMain#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#3)]

> [!NOTE]
> Bir Windows Forms uygulamasındaki yönteminde komut satırı bağımsız değişkenlerini etkinleştirmek için `Main` , program.cs içindeki imzasını el ile değiştirmeniz gerekir `Main` . *program.cs* Windows Forms Tasarımcısı tarafından oluşturulan kod, `Main` giriş parametresi olmadan bir oluşturur. Ayrıca <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> , komut satırı bağımsız değişkenlerine konsol veya Windows uygulamasındaki herhangi bir noktadan erişmek için de kullanabilirsiniz.

Yönteminin parametresi, `Main` <xref:System.String> komut satırı bağımsız değişkenlerini temsil eden bir dizidir. Genellikle, özelliği test ederek bağımsız değişkenlerin mevcut olup olmadığını belirlersiniz `Length` . Örneğin:

[!code-csharp[csProgGuideMain#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#4)]

> [!TIP]
> `args`Dizi null olamaz. Bu nedenle, `Length` özelliği null denetimi olmadan erişmek güvenlidir.

Ayrıca, sınıfını veya yöntemini kullanarak dize bağımsız değişkenlerini sayısal türlere dönüştürebilirsiniz <xref:System.Convert> `Parse` . Örneğin, aşağıdaki ifade, `string` `long` yöntemini kullanarak öğesini bir sayıya dönüştürür <xref:System.Int64.Parse%2A> :

```csharp
long num = Int64.Parse(args[0]);
```

C# türü de kullanılabilir `long` , diğer ad `Int64` :

```csharp
long num = long.Parse(args[0]);
```

`Convert` `ToInt64` Aynı şeyi yapmak için de sınıf yöntemini kullanabilirsiniz:

```csharp
long num = Convert.ToInt64(s);
```

Daha fazla bilgi için <xref:System.Int64.Parse%2A> ve <xref:System.Convert> bölümlerine bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir konsol uygulamasında komut satırı bağımsız değişkenlerinin nasıl kullanılacağını gösterir. Uygulama çalışma zamanında bir bağımsız değişken alır, bağımsız değişkeni bir tamsayıya dönüştürür ve sayının faktöriyelini hesaplar. Bağımsız değişken sağlanmazsa, uygulama programın doğru kullanımını açıklayan bir ileti yayınlar.

Uygulamayı bir komut isteminden derlemek ve çalıştırmak için aşağıdaki adımları izleyin:

1. Aşağıdaki kodu herhangi bir metin düzenleyicisine yapıştırın ve sonra dosyayı *Factorial.cs*adlı bir metin dosyası olarak kaydedin.

     [!code-csharp[csProgGuideMain#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#16)]

2. **Başlat** ekranından veya **Başlat** menüsünden bir Visual Studio **Geliştirici komut istemi** penceresi açın ve ardından yeni oluşturduğunuz dosyayı içeren klasöre gidin.

3. Uygulamayı derlemek için aşağıdaki komutu girin.
  
     `csc Factorial.cs`  
  
     Uygulamanızda hiçbir derleme hatası yoksa, *Factorial.exe* adlı yürütülebilir bir dosya oluşturulur.
  
4. 3 ' ün çarpımını hesaplamak için aşağıdaki komutu girin:
  
     `Factorial 3`  
  
5. Komut bu çıktıyı üretir:`The factorial of 3 is 6.`

> [!NOTE]
> Visual Studio 'da bir uygulama çalıştırırken, [hata ayıklama sayfasında, proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer)' nda komut satırı bağımsız değişkenlerini belirtebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Environment?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Main () ve komut satırı bağımsız değişkenleri](index.md)
- [Komut satırı bağımsız değişkenlerini görüntüleme](how-to-display-command-line-arguments.md)
- [Ana() Dönüş Değerleri](main-return-values.md)
- [Sınıflar](../classes-and-structs/classes.md)
