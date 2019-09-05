---
title: Komut satırı bağımsız değişkenleri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: 6f071f907fe38b226a5083699e758bc5fb8bffce
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252988"
---
# <a name="command-line-arguments-c-programming-guide"></a>Komut Satırı Bağımsız Değişkenleri (C# Programlama Kılavuzu)
Yöntemi aşağıdaki yöntemlerden biriyle tanımlayarak `Main` yöntemine bağımsız değişkenler gönderebilirsiniz:  
  
 [!code-csharp[csProgGuideMain#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#2)]  
  
 [!code-csharp[csProgGuideMain#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#3)]  
  
> [!NOTE]
> Bir Windows Forms uygulamasındaki `Main` yönteminde komut satırı bağımsız değişkenlerini etkinleştirmek için, program.cs `Main` içindeki imzasını el ile değiştirmeniz gerekir. Windows Forms Tasarımcısı tarafından oluşturulan kod, giriş parametresi olmadan `Main` bir oluşturur. Ayrıca, komut satırı <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> bağımsız <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> değişkenlerine konsol veya Windows uygulamasındaki herhangi bir noktadan erişmek için de kullanabilirsiniz.  
  
 `Main` Yönteminin parametresi, komut satırı bağımsız değişkenlerini <xref:System.String> temsil eden bir dizidir. Genellikle, `Length` özelliği test ederek bağımsız değişkenlerin mevcut olup olmadığını belirlersiniz. Örneğin:  
  
 [!code-csharp[csProgGuideMain#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#4)]  
  
 Ayrıca, <xref:System.Convert> sınıfını `Parse` veya yöntemini kullanarak dize bağımsız değişkenlerini sayısal türlere dönüştürebilirsiniz. Örneğin, aşağıdaki ifade, `string` <xref:System.Int64.Parse%2A> yöntemini kullanarak öğesini bir `long` sayıya dönüştürür:  
  
```csharp  
long num = Int64.Parse(args[0]);  
```  
  
 Ayrıca, şu diğer adlar C# `long` `Int64`kullanılarak türü de kullanabilirsiniz:  
  
```csharp  
long num = long.Parse(args[0]);  
```  
  
 Aynı şeyi yapmak için de `Convert` sınıf yöntemini `ToInt64` kullanabilirsiniz:  
  
```csharp  
long num = Convert.ToInt64(s);  
```  
  
 Daha fazla bilgi için bkz. <xref:System.Int64.Parse%2A> ve <xref:System.Convert>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir konsol uygulamasında komut satırı bağımsız değişkenlerinin nasıl kullanılacağını gösterir. Uygulama çalışma zamanında bir bağımsız değişken alır, bağımsız değişkeni bir tamsayıya dönüştürür ve sayının faktöriyelini hesaplar. Bağımsız değişken sağlanmazsa, uygulama programın doğru kullanımını açıklayan bir ileti yayınlar.  
  
 Uygulamayı bir komut isteminden derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. Aşağıdaki kodu herhangi bir metin düzenleyicisine yapıştırın ve sonra dosyayı adlı `Factorial.cs`bir metin dosyası olarak kaydedin.  
  
     [!code-csharp[csProgGuideMain#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#16)]  
  
2. **Başlat** ekranından veya **Başlat** menüsünden bir Visual Studio **Geliştirici komut istemi** penceresi açın ve ardından yeni oluşturduğunuz dosyayı içeren klasöre gidin.  
  
3. Uygulamayı derlemek için aşağıdaki komutu girin.  
  
     `csc Factorial.cs`  
  
     Uygulamanızda hiçbir derleme hatası yoksa, adında `Factorial.exe` bir yürütülebilir dosya oluşturulur.  
  
4. 3 ' ün çarpımını hesaplamak için aşağıdaki komutu girin:  
  
     `Factorial 3`  
  
5. Komut bu çıktıyı üretir:`The factorial of 3 is 6.`  
  
> [!NOTE]
> Visual Studio 'da bir uygulama çalıştırırken, [hata ayıklama sayfasında, proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer)' nda komut satırı bağımsız değişkenlerini belirtebilirsiniz.  
  
 Komut satırı bağımsız değişkenlerinin nasıl kullanılacağı hakkında daha fazla örnek için bkz [. nasıl yapılır: Komut satırını](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)kullanarak derlemeleri oluşturun ve kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Environment?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](./index.md)
- [Nasıl yapılır: Komut satırı bağımsız değişkenlerini görüntüle](./how-to-display-command-line-arguments.md)
- [Ana() Dönüş Değerleri](./main-return-values.md)
- [Sınıflar](../classes-and-structs/classes.md)
