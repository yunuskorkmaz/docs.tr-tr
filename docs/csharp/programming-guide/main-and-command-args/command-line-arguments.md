---
title: Komut Satırı Bağımsız Değişkenleri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: a55e40a4a4880c39c74186c55b0886e06dc33bcb
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884832"
---
# <a name="command-line-arguments-c-programming-guide"></a>Komut Satırı Bağımsız Değişkenleri (C# Programlama Kılavuzu)
Bağımsız değişken gönderebilirsiniz `Main` yöntemi aşağıdaki yöntemlerden biriyle tanımlayarak yöntemi:  
  
 [!code-csharp[csProgGuideMain#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_1.cs)]  
  
 [!code-csharp[csProgGuideMain#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_2.cs)]  
  
> [!NOTE]
>  Komut satırı bağımsız değişkenlerini etkinleştirmek için `Main` yöntemi bir Windows Forms uygulamasındaki el ile değiştirmeniz gerekir imzası `Main` program.CS'de webhostbuilder'a. Windows Forms Tasarımcısı tarafından oluşturulan kod oluşturur bir `Main` girdi parametresi olmadan. Ayrıca <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> veya <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> konsolda veya Windows uygulama herhangi bir noktasından komut satırı bağımsız değişkenleri erişmek için.  
  
 Parametresi `Main` yöntemi bir <xref:System.String> komut satırı bağımsız değişkenlerini temsil eden bir dizi. Genellikle, test ederek bağımsız değişkenleri var olup olmadığını belirlemeniz `Length` özelliği, örneğin:  
  
 [!code-csharp[csProgGuideMain#4](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_3.cs)]  
  
 Kullanarak dize bağımsız değişkenlerini sayısal türlere de dönüştürebilirsiniz <xref:System.Convert> sınıfı veya `Parse` yöntemi. Örneğin, aşağıdaki deyim dönüştürür `string` için bir `long` numarası kullanarak <xref:System.Int64.Parse%2A> yöntemi:  
  
```  
long num = Int64.Parse(args[0]);  
```  
  
 C# türü kullanmak da mümkündür `long`, hangi diğer adların `Int64`:  
  
```  
long num = long.Parse(args[0]);  
```  
  
 Ayrıca `Convert` sınıfı yöntemi `ToInt64` aynı şeyi yapmak için:  
  
```  
long num = Convert.ToInt64(s);  
```  
  
 Daha fazla bilgi için bkz. <xref:System.Int64.Parse%2A> ve <xref:System.Convert>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir konsol uygulamasında komut satırı bağımsız değişkenleri kullanmayı gösterir. Uygulama çalışma zamanında bir bağımsız değişken alır, bağımsız değişkeni bir tamsayıya dönüştürür ve sayının faktöriyelini hesaplar. Bağımsız değişken sağlanmadıysa uygulama programın doğru kullanımını açıklayan bir ileti verir.  
  
 Derleme ve uygulamayı bir komut istemi'nden çalıştırmak için bu adımları izleyin:  
  
1.  Aşağıdaki kodu herhangi bir metin düzenleyiciye yapıştırın ve dosyayı ada sahip bir metin dosyası olarak kaydedin `Factorial.cs`.  
  
     [!code-csharp[csProgGuideMain#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_4.cs)]  
  
2.  Gelen **Başlat** ekran veya **Başlat** menüsünde, Visual Studio'yu açın **Geliştirici komut istemi** penceresini ve ardından yeni dosyasını içeren klasöre gidin oluşturuldu.  
  
3.  Uygulamayı derlemek üzere aşağıdaki komutu girin.  
  
     `csc Factorial.cs`  
  
     Uygulamanızın adında bir yürütülebilir dosya hiç derleme hatası varsa `Factorial.exe` oluşturulur.  
  
4.  3'ün faktoriyelini hesaplamak için aşağıdaki komutu girin:  
  
     `Factorial 3`  
  
5.  Komut şu çıktıyı üretir: `The factorial of 3 is 6.`  
  
> [!NOTE]
>  Visual Studio'da bir uygulama çalıştırırken, komut satırı bağımsız değişkenlerinde belirtebilirsiniz [hata ayıklama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer).  
  
 Komut satırı bağımsız değişkenlerinin nasıl kullanılacağı hakkında daha fazla örnek için bkz. [nasıl yapılır: komut satırı kullanan derlemeler kullanma ve oluşturma](../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Environment?displayProperty=nameWithType>  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [Nasıl yapılır: Komut Satırı Bağımsız Değişkenlerini Görüntüleme](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
- [Nasıl yapılır: foreach Kullanarak Komut Satırı Bağımsız Değişkenlerine Erişme](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
- [Ana() Dönüş Değerleri](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)  
- [Sınıflar](../../../csharp/programming-guide/classes-and-structs/classes.md)
