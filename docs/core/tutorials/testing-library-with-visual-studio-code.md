---
title: Visual Studio Code kullanarak .NET sınıf kitaplığı test etme
description: .NET sınıf kitaplığı için bir birim testi projesi oluşturmak ve çalıştırmak üzere Visual Studio Code ve .NET CLı 'yi nasıl kullanacağınızı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: 4528bd203ae03988a1d1d80a7e904e94e68c1d04
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94915862"
---
# <a name="tutorial-test-a-net-class-library-using-visual-studio-code"></a>Öğretici: Visual Studio Code kullanarak .NET sınıf kitaplığı test etme

Bu öğreticide, bir çözüme test projesi ekleyerek birim testinin nasıl otomatikleştirilmesi gösterilmektedir.

## <a name="prerequisites"></a>Önkoşullar

- Bu öğretici, [Visual Studio Code kullanarak bir .NET sınıf kitaplığı oluşturma](library-with-visual-studio-code.md)bölümünde oluşturduğunuz çözümle birlikte kullanılır.

## <a name="create-a-unit-test-project"></a>Birim testi projesi oluşturma

Birim testleri geliştirme ve yayımlama sırasında otomatik yazılım testi sağlar. Bu öğreticide kullandığınız test çerçevesi MSTest. [MSTest](https://github.com/Microsoft/testfx-docs) , aralarından seçim yapabileceğiniz üç test çerçevelerinden biridir. Diğerleri [xUnit](https://xunit.net/) ve [NUnit](https://nunit.org/)' dir.

1. Visual Studio Code’u başlatın.

1. `ClassLibraryProjects` [Visual Studio Code kullanarak .NET sınıf kitaplığı oluşturma](library-with-visual-studio-code.md)bölümünde oluşturduğunuz çözümü açın.

1. "StringLibraryTest" adlı bir birim testi projesi oluşturun.

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   Proje şablonu aşağıdaki kodla bir UnitTest1.cs dosyası oluşturur:

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   Birim testi şablonu tarafından oluşturulan kaynak kodu aşağıdakileri yapar:

   - <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>Birim testi için kullanılan türleri içeren ad alanını içeri aktarır.
   - <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>Özniteliği `UnitTest1` sınıfına uygular.
   - <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>Tanımlamak için özniteliğini uygular `TestMethod1` .

   [ [TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) ile etiketlenmiş bir test sınıfında [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) etiketli her bir yöntem, birim testi çalıştırıldığında otomatik olarak yürütülür.

1. Çözüme test projesi ekleyin.

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

## <a name="add-a-project-reference"></a>Proje başvurusu Ekle

Test projesinin sınıfla çalışması için projeye `StringLibrary` bir başvuru ekleyin `StringLibraryTest` `StringLibrary` .

1. Şu komutu çalıştırın:

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

## <a name="add-and-run-unit-test-methods"></a>Birim testi yöntemleri ekleme ve çalıştırma

Visual Studio bir birim testi çalıştırdığında, özniteliğiyle <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> işaretlenmiş bir sınıfta özniteliğiyle işaretlenmiş her metodu yürütür  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> . İlk hata bulunduğunda veya yöntemde bulunan tüm testler başarılı olduğunda bir test yöntemi sonlanır.

En yaygın testler, sınıfının üyelerini çağırır <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> . Birçok onaylama yöntemi, biri beklenen test sonucu ve diğeri de gerçek test sonucu olan en az iki parametre içerir. `Assert`Sınıfın en sık çağrılan yöntemlerin bazıları aşağıdaki tabloda gösterilmiştir:

| Onaylama yöntemleri     | İşlev |
| ------------------ | -------- |
| `Assert.AreEqual`  | İki değerin veya nesnenin eşit olduğunu doğrular. Değerler veya nesneler eşitse onaylama başarısız olur. |
| `Assert.AreSame`   | İki nesne değişkeninin aynı nesneye başvurmasını doğrular. Değişkenler farklı nesnelere başvuru yaptığında onaylama başarısız olur. |
| `Assert.IsFalse`   | Bir koşulun olduğunu doğrular `false` . Koşul ise onaylama başarısız olur `true` . |
| `Assert.IsNotNull` | Bir nesnenin olmadığını doğrular `null` . Nesne ise onaylama başarısız olur `null` . |

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>Yöntemi bir test yönteminde, oluşturması beklenen özel durum türünü belirtmek için de kullanabilirsiniz. Belirtilen özel durum atılmazsa, test başarısız olur.

Yöntemi test ederken `StringLibrary.StartsWithUpper` , büyük harf karakteriyle başlayan bir dizi dize sağlamak istersiniz. Yöntemi bu durumlarda Return olarak beklediğinizi ve `true` <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> yöntemi çağırabilirsiniz. Benzer şekilde, büyük harfli bir karakter ile başlayan bir dizi dize sağlamak istersiniz. Yöntemi bu durumlarda Return olarak beklediğinizi ve `false` <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> yöntemi çağırabilirsiniz.

Kitaplık yönteminiz dizeleri yaptığından, ayrıca [boş bir dizeyi ( `String.Empty` )](xref:System.String.Empty) ve ve bir dizeyi başarılı bir şekilde işlediğinden emin olmak istersiniz `null` . Boş bir dize, karakteri olmayan ve 0 olan bir dizedir <xref:System.String.Length> . Bir `null` dize başlatılmamış bir dizedir. `StartsWithUpper`Doğrudan statik bir yöntem olarak çağırabilir ve tek bir <xref:System.String> bağımsız değişken geçirebilirsiniz. Ya da `StartsWithUpper` öğesine atanan bir değişkende bir genişletme yöntemi olarak çağırabilirsiniz `string` `null` .

Her biri <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> bir dize dizisindeki her öğe için bir yöntem çağıran üç yöntem tanımlayacaksınız. Test hatası durumunda görüntülenecek bir hata iletisi belirtmenize imkan tanıyan bir yöntem aşırı yüklemesi çağıracaksınız. İleti, hataya neden olan dizeyi tanımlar.

Test yöntemleri oluşturmak için:

1. *Stringlibrarytest/UnitTest1. cs* ' i açın ve tüm kodu aşağıdaki kodla değiştirin.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   Yöntemdeki büyük harfli karakterlerin testi, `TestStartsWithUpper` Yunanca Büyük Harf Alpha (u + 0391) ve Kiril Büyük harf em (u + 041C) içerir. Yöntemdeki küçük harfli karakterlerin testi `TestDoesNotStartWithUpper` Yunanca Küçük Harf Alpha (u + 03B1) ve Kiril Küçük harf GHE (u + 0433) içerir.

1. Yaptığınız değişiklikleri kaydedin.

1. Testleri çalıştırın:

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   Terminal çıktısı tüm testlerin geçtiğini gösterir.

   ```output
   Starting test execution, please wait...
   A total of 1 test files matched the specified pattern.

   Passed!  - Failed:     0, Passed:     3, Skipped:     0, Total:     3, Duration: 3 ms - StringLibraryTest.dll (net5.0)
   ```

## <a name="handle-test-failures"></a>Test başarısızlıklarını işle

Test odaklı geliştirme (TDD) yapıyorsanız, önce testleri yazarsınız ve ilk kez çalıştırdığınızda başarısız olur. Sonra, uygulamayı başarılı hale getiren uygulamaya kod eklersiniz. Bu öğreticide, doğrulaması yaptığı uygulama kodunu yazdıktan sonra test başarısız olduğunu görmediyseniz testi oluşturdunuz. Başarısız olması beklendiğinde testin başarısız olduğunu doğrulamak için, test girişine geçersiz bir değer ekleyin.

1. `words`Yöntemdeki diziyi, `TestDoesNotStartWithUpper` "Error" dizesini içerecek şekilde değiştirin.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. Testleri çalıştırın:

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   Terminal çıktısı bir testin başarısız olduğunu gösterir ve başarısız test için bir hata iletisi sağlar: "onaylama. IsFalse başarısız oldu. ' Error ' bekleniyor: false; gerçek: true ". Hata nedeniyle "hata" sonunda dizide hiçbir dize sınanmadı.

   ```output
   Starting test execution, please wait...
   A total of 1 test files matched the specified pattern.
     Failed TestDoesNotStartWithUpper [28 ms]
     Error Message:
      Assert.IsFalse failed. Expected for 'Error': false; Actual: True
     Stack Trace:
        at StringLibraryTest.UnitTest1.TestDoesNotStartWithUpper() in C:\ClassLibraryProjects\StringLibraryTest\UnitTest1.cs:line 33

   Failed!  - Failed:     1, Passed:     2, Skipped:     0, Total:     3, Duration: 31 ms - StringLibraryTest.dll (net5.0)
   ```

1. Adım 1 ' de eklediğiniz "Error" dizesini kaldırın. Testi ve test geçişini yeniden çalıştırın.

## <a name="test-the-release-version-of-the-library"></a>Kitaplığın yayın sürümünü test etme

Artık, kitaplığın hata ayıklama derlemesini çalıştırırken testlerin başarılı olduğuna göre, bu testleri kitaplığın yayın derlemesi için ek bir zaman çalıştırın. Derleyici iyileştirmeleri dahil olmak üzere bir dizi etken bazen hata ayıklama ve yayın yapıları arasında farklı davranışlar üretebilir.

1. Testleri yayın yapı yapılandırmasıyla çalıştırın:

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   Testler geçer.

## <a name="debug-tests"></a>Hata ayıklama testleri

IDE 'niz olarak Visual Studio Code kullanıyorsanız, birim testi projenizi kullanarak kodun hatalarını ayıklamak için [Visual Studio Code kullanarak bir .NET konsol uygulamasında hata ayıklama](debugging-with-visual-studio-code.md) sırasında gösterilen aynı işlemi kullanabilirsiniz. *Gösterimi* uygulama projesini başlatmak yerine *stringlibrarytest/UnitTest1. cs* açın ve 7 ve 8 satırları arasında **Tüm Testleri Çalıştır** ' ı seçin. Bunu bulamıyorsanız, <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>P</kbd> tuşlarına basarak komut paletini açın ve **yeniden yükle penceresini** girin.

Visual Studio Code, test projesini hata ayıklayıcı ekli olarak başlatır. Yürütme, test projesine veya temeldeki kitaplık koduna eklediğiniz herhangi bir kesme noktasında durur.

## <a name="additional-resources"></a>Ek kaynaklar

* [.NET 'te birim testi](../testing/index.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, birim bir sınıf kitaplığı test edilmiştir. Bir paket olarak [NuGet](https://nuget.org) 'e yayımlayarak, kitaplığı başkaları için kullanılabilir hale getirebilirsiniz. Nasıl yapılacağını öğrenmek için bir NuGet öğreticisini izleyin:

> [!div class="nextstepaction"]
> [DotNet CLı kullanarak bir paket oluşturma ve yayımlama](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

Bir kitaplığı bir NuGet paketi olarak yayımlarsanız, diğerleri onu yükleyebilir ve kullanabilir. Nasıl yapılacağını öğrenmek için bir NuGet öğreticisini izleyin:

> [!div class="nextstepaction"]
> [DotNet CLı kullanarak bir paket yükleyip kullanma](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

Bir kitaplığın paket olarak dağıtılması gerekmez. Onu kullanan bir konsol uygulamasıyla paketlenmiş olabilir. Bir konsol uygulamasını yayımlamayı öğrenmek için bu serideki önceki öğreticiye bakın:

> [!div class="nextstepaction"]
> [Visual Studio Code kullanarak bir .NET konsol uygulaması yayımlama](publishing-with-visual-studio-code.md)
