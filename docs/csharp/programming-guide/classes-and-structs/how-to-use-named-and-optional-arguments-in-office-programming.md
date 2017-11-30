---
title: "Nasıl yapılır: Office Programlamada Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenleri Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
caps.latest.revision: "34"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a453699591397224435fba1e602c305f18e84a11
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a>Nasıl yapılır: Office Programlamada Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenleri Kullanma (C# Programlama Kılavuzu)
Adlandırılmış bağımsız değişkenler ve isteğe bağlı bağımsız değişkenler de kullanıma sunulan [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], kolaylık, esneklik ve C# programlama okunabilirliğini artırmak. Ayrıca, bu özellikler, Microsoft Office Otomasyonu API'leri gibi COM arabirimlerine erişim büyük ölçüde kolaylaştırır.  
  
 Aşağıdaki örnekte, yöntem [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) altı gibi biçimlendirme, satırları ve sütunları sayısını sınırlayan bir tablo özelliklerini temsil eden parametreleri, yazı tiplerini ve renkleri vardır. Çoğu zaman, bunların tümünün için özel değerler belirtmek istemediğiniz tüm altı parametreler isteğe bağlıdır. Ancak, adlandırılmış ve isteğe bağlı bağımsız değişkenler bir değer veya bir yer tutucu değerini her parametre için sağlanması gerekir. Adlandırılmış ve isteğe bağlı bağımsız değişkenlerle projeniz için gerekli olan parametreleri için değerleri belirtin.  
  
 Bu yordamları tamamlamak için Microsoft Office Word, bilgisayarınızda yüklü olması gerekir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a>Yeni bir konsol uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın.  
  
2.  Üzerinde **dosya** menüsündeki **yeni**ve ardından **proje**.  
  
3.  İçinde **şablon kategorileri** bölmesini genişletin **Visual C#**ve ardından **Windows**.  
  
4.  Üst kısmındaki Ara **şablonları** emin olmak için bölmesinde **.NET Framework 4** görünür **hedef Framework** kutusu.  
  
5.  İçinde **şablonları** bölmesinde tıklatın **konsol uygulaması**.  
  
6.  Projenizde için bir ad yazın **adı** alan.  
  
7.  **Tamam**'ı tıklatın.  
  
     Yeni Proje görünür **Çözüm Gezgini**.  
  
### <a name="to-add-a-reference"></a>Başvuru eklemek için  
  
1.  İçinde **Çözüm Gezgini**, projenizin adına sağ tıklayın ve ardından **Başvuru Ekle**. **Başvuru Ekle** iletişim kutusu görüntülenir.  
  
2.  Üzerinde **.NET** sayfasında, **Microsoft.Office.Interop.Word** içinde **bileşen adı** listesi.  
  
3.  **Tamam**'ı tıklatın.  
  
### <a name="to-add-necessary-using-directives"></a>Eklemek için gerekli yönergeleri kullanma  
  
1.  İçinde **Çözüm Gezgini**, sağ **Program.cs** dosya ve ardından **görünümü kodu**.  
  
2.  Aşağıdakileri ekleyin `using` yönergelerini kod dosyasının en üstüne.  
  
     [!code-csharp[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]  
  
### <a name="to-display-text-in-a-word-document"></a>Bir Word belgesinde metni görüntülemek için  
  
1.  İçinde `Program` sınıf Program.cs içinde bir Word uygulaması ve bir Word belgesi oluşturmak için aşağıdaki yöntemi ekleyin. [Ekle](http://go.microsoft.com/fwlink/?LinkId=145381) yöntemi dört isteğe bağlı parametre vardır. Bu örnek, varsayılan değerleri kullanır. Bu nedenle, bağımsız değişkenler arama deyiminde gerekli değildir.  
  
     [!code-csharp[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]  
  
2.  Aşağıdaki kodu nereye belgedeki metin görüntülemek ve görüntülenecek metni tanımlamak için yöntemi sonuna ekleyin.  
  
     [!code-csharp[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]  
  
### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için  
  
1.  Aşağıdaki deyim ana ekleyin.  
  
     [!code-csharp[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]  
  
2.  Projeyi çalıştırmak için CTRL + F5 tuşuna basın. Belirtilen metni içeren bir Word belgesi görünür.  
  
### <a name="to-change-the-text-to-a-table"></a>Bir tabloya metni değiştirmek için  
  
1.  Kullanım `ConvertToTable` yöntemi bir tablodaki metni alın. Yöntemi, altı isteğe bağlı parametre yok. IntelliSense aşağıdaki çizimde gösterildiği gibi isteğe bağlı parametreler köşeli parantez içine alır.  
  
     ![ConvertToTable yönteminin listesi. ] (../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")  
ConvertToTable parametreleri  
  
     Adlandırılmış ve isteğe bağlı bağımsız değişkenler, değiştirmek istediğiniz parametre değerlerini belirtmenize olanak verir. Yönteminin sonuna aşağıdaki kodu ekleyin `DisplayInWord` basit bir tablo oluşturmak için. Metinde virgüller içinde dize bağımsız değişkeni belirtir `range` tablo hücrelerinin ayırın.  
  
     [!code-csharp[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]  
  
     Önceki sürümlerinde, C#, çağrısı `ConvertToTable` aşağıdaki kodda gösterildiği gibi her parametre için bir başvuru bağımsız değişken gerektirir.  
  
     [!code-csharp[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]  
  
2.  Projeyi çalıştırmak için CTRL + F5 tuşuna basın.  
  
### <a name="to-experiment-with-other-parameters"></a>Diğer parametrelerle denemek için  
  
1.  Bir sütun ve üç satır sahip olması tabloyu değiştirmek için son satırında yerini `DisplayInWord` aşağıdaki ifadeyi ve CTRL + F5'e yazın.  
  
     [!code-csharp[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]  
  
2.  Tablosu için önceden tanımlanmış bir biçim belirtmek için son satırında Değiştir `DisplayInWord` aşağıdaki ifadeyi ve CTRL + F5'e yazın. Biçim herhangi biri olabilir [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) sabitleri.  
  
     [!code-csharp[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tam örnek içerir.  
  
 [!code-csharp[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Adlandırılmış ve isteğe bağlı bağımsız değişkenler](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
