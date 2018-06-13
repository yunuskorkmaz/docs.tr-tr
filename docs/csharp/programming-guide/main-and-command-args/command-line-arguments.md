---
title: Komut Satırı Bağımsız Değişkenleri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: 92b3f916b58f72ab2f2f542d3a611d35861afebe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335331"
---
# <a name="command-line-arguments-c-programming-guide"></a>Komut Satırı Bağımsız Değişkenleri (C# Programlama Kılavuzu)
Bağımsız değişkenleri gönderebilirsiniz `Main` yöntemi aşağıdaki yollardan biriyle tanımlayarak yöntemi:  
  
 [!code-csharp[csProgGuideMain#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_1.cs)]  
  
 [!code-csharp[csProgGuideMain#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_2.cs)]  
  
> [!NOTE]
>  Komut satırı bağımsız değişkenleri olarak etkinleştirmek için `Main` yöntemi bir Windows Forms uygulamasında el ile değiştirmeniz gerekir imzası `Main` program.cs içinde. Windows Forms Tasarımcısı tarafından oluşturulan kodu oluşturur bir `Main` bir giriş parametresi olmadan. Aynı zamanda <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> veya <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> konsolu veya Windows uygulama herhangi bir noktasından komut satırı bağımsız değişkenleri erişmek için.  
  
 Parametresi, `Main` yöntemi bir <xref:System.String> komut satırı değişkenlerini temsil eden bir dizi. Genellikle, bağımsız değişkenler test ederek olup olmadığını belirleme `Length` özelliği, örneğin:  
  
 [!code-csharp[csProgGuideMain#4](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_3.cs)]  
  
 Kullanarak sayısal türler dize bağımsız değişkenleri dönüştürebilirsiniz <xref:System.Convert> sınıfı veya `Parse` yöntemi. Örneğin aşağıdaki deyim dönüştürür `string` için bir `long` kullanarak sayı <xref:System.Int64.Parse%2A> yöntemi:  
  
```  
long num = Int64.Parse(args[0]);  
```  
  
 C# türü kullanmak da mümkündür `long`, hangi diğer adların `Int64`:  
  
```  
long num = long.Parse(args[0]);  
```  
  
 Aynı zamanda `Convert` sınıf yöntemi `ToInt64` aynı şeyi yapmak için:  
  
```  
long num = Convert.ToInt64(s);  
```  
  
 Daha fazla bilgi için bkz. <xref:System.Int64.Parse%2A> ve <xref:System.Convert>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir konsol uygulamasında komut satırı bağımsız değişkenleri kullanmayı gösterir. Uygulama çalışma zamanında bir bağımsız değişkeni alır, bağımsız değişkeni bir tamsayıya dönüştürür ve sayının faktöriyelini hesaplar. Bağımsız değişkenler sağlandıysa, uygulama programı'nın doğru kullanımını açıklayan bir ileti yayımlar.  
  
 Derleme ve uygulamayı bir komut isteminden çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Aşağıdaki kod bir metin düzenleyicisine yapıştırın ve dosyayı ada sahip bir metin dosyası olarak kaydedin `Factorial.cs`.  
  
     [!code-csharp[csProgGuideMain#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_4.cs)]  
  
2.  Gelen **Başlat** ekran veya **Başlat** menüsünde, Visual Studio'yu açın **Geliştirici komut istemi** penceresinde ve ardından yeni dosyasını içeren klasöre gidin oluşturulur.  
  
3.  Uygulamayı derlemek için aşağıdaki komutu girin.  
  
     `csc Factorial.cs`  
  
     Adlı bir yürütülebilir dosya hiç derleme hatası uygulamanız varsa, `Factorial.exe` oluşturulur.  
  
4.  3 çarpımını hesaplamak için aşağıdaki komutu girin:  
  
     `Factorial 3`  
  
5.  Komutu, bu çıktı üretir: `The factorial of 3 is 6.`  
  
> [!NOTE]
>  Bir uygulamayı Visual Studio'da çalıştırırken, komut satırı bağımsız değişkenleri belirtebilirsiniz [hata ayıklama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer).  
  
 Komut satırı bağımsız değişkenleri kullanma hakkında daha fazla örnek için bkz: [nasıl yapılır: oluşturma ve kullanma derlemeler kullanma komut satırı](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Environment?displayProperty=nameWithType>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Ana() ve Komut Satırı Bağımsız Değişkenleri](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Nasıl yapılır: Komut Satırı Bağımsız Değişkenlerini Görüntüleme](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [Nasıl yapılır: foreach Kullanarak Komut Satırı Bağımsız Değişkenlerine Erişme](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Ana() Dönüş Değerleri](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)  
 [Sınıflar](../../../csharp/programming-guide/classes-and-structs/classes.md)
