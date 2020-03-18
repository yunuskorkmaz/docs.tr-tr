---
title: Office programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenler nasıl kullanılır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 36b5c8b49404606c8240d24953c3677d5612d30e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714869"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a>Office programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenler nasıl kullanılır (C# Programlama Kılavuzu)

C# 4'te tanıtılan adlandırılmış bağımsız değişkenler ve isteğe bağlı bağımsız değişkenler, C# programlamada kolaylığı, esnekliği ve okunabilirliği artırır. Ayrıca, bu özellikler Microsoft Office otomasyon API'leri gibi COM arabirimlerine erişimi büyük ölçüde kolaylaştırır.

Aşağıdaki örnekte, [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) yöntemi, sütun ve satır sayısı, biçimlendirme, kenarlıklar, yazı tipleri ve renkler gibi bir tablonun özelliklerini temsil eden on altı parametreye sahiptir. Çoğu zaman hepsi için belirli değerleri belirtmek istemediğiniz için on altı parametrenin tümü isteğe bağlıdır. Ancak, adlandırılmış ve isteğe bağlı bağımsız değişkenler olmadan, her parametre için bir değer veya yer tutucu değeri sağlanmalıdır. Adlandırılmış ve isteğe bağlı bağımsız değişkenlerle, yalnızca projeniz için gerekli parametreler için değerleri belirtirsiniz.

Bu yordamları tamamlamak için bilgisayarınızda Microsoft Office Word yüklü olması gerekir.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a>Yeni bir konsol uygulaması oluşturmak için

1. Visual Studio’yu çalıştırın.

2. **Dosya** menüsünde **Yeni'yi**işaret edin ve ardından **Project'i**tıklatın.

3. **Şablonlar Kategorileri** bölmesinde **Visual C#** seçeneğini genişletin ve **ardından Windows'u**tıklatın.

4. **.NET Framework 4'ün** **Hedef Çerçeve** kutusunda göründüğünden emin olmak için **Şablonlar** bölmesinin üst bölümüne bakın.

5. **Şablonlar** bölmesinde Konsol **Uygulaması'nı**tıklatın.

6. **Ad** alanına projeniz için bir ad yazın.

7. **Tamam**'a tıklayın.

     Yeni proje Çözüm **Gezgini'nde**görünür.

## <a name="to-add-a-reference"></a>Başvuru eklemek için

1. **Çözüm Gezgini'nde,** projenizin adını sağ tıklatın ve ardından **Başvuru Ekle'yi**tıklatın. **Başvuru Ekle** iletişim kutusu görüntülenir.

2. **.NET** sayfasında, **Bileşen Adı** listesinde **Microsoft.Office.Interop.Word'u** seçin.

3. **Tamam**'a tıklayın.

## <a name="to-add-necessary-using-directives"></a>Yönergeleri kullanarak gerekli eklemek için

1. **Çözüm Gezgini'nde,** *Program.cs* dosyasını sağ tıklatın ve ardından **Kodu Görüntüle'yi**tıklatın.

2. Kod dosyasının üst bölümüne aşağıdaki `using` yönergeleri ekleyin:

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a>Word belgesinde metni görüntülemek için

1. `Program` *Program.cs'daki*sınıfta, Word uygulaması ve Word belgesi oluşturmak için aşağıdaki yöntemi ekleyin. [Ekle](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) yönteminin dört isteğe bağlı parametresi vardır. Bu örnekte varsayılan değerleri kullanır. Bu nedenle, arama deyiminde bağımsız değişken gerekmez.

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. Belgede metnin nerede görüntüleneği ve hangi metnin görüntüleneleyeceğini tanımlamak için yöntemin sonuna aşağıdaki kodu ekleyin:

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için

1. Main'e aşağıdaki ifadeyi ekleyin:

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. Projeyi çalıştırmak için <kbd>CTRL</kbd>+<kbd>F5</kbd> tuşuna basın. Belirtilen metni içeren bir Word belgesi görüntülenir.

## <a name="to-change-the-text-to-a-table"></a>Metni tabloya değiştirmek için
  
1. Metni `ConvertToTable` bir tabloya bünyesine katmayı yapmak için yöntemi kullanın. Yöntemon on altı isteğe bağlı parametre vardır. IntelliSense, aşağıdaki resimde gösterildiği gibi isteğe bağlı parametreleri parantez içine içine alar.

     ![ConvertToTable yöntemi için parametrelerlistesi](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     Adlandırılmış ve isteğe bağlı bağımsız değişkenler, yalnızca değiştirmek istediğiniz parametreler için değerleri belirtmenize olanak tanır. Basit bir tablo oluşturmak için `DisplayInWord` yöntemin sonuna aşağıdaki kodu ekleyin. Bağımsız değişken, metin dizesindeki virgüllerin tablonun hücrelerini `range` birbirinden ayırdığını belirtir.

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     C#'ın önceki sürümlerinde, `ConvertToTable` çağrı, aşağıdaki kodda gösterildiği gibi, her parametre için bir başvuru bağımsız değişkeni gerektirir:
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. Projeyi çalıştırmak için <kbd>CTRL</kbd>+<kbd>F5</kbd> tuşuna basın.

## <a name="to-experiment-with-other-parameters"></a>Diğer parametrelerle denemeler yapmak için

1. Tabloyu bir sütun ve üç satır olacak şekilde değiştirmek için, son satırı `DisplayInWord` aşağıdaki deyimle değiştirin ve ardından <kbd>CTRL</kbd>+<kbd>F5</kbd>yazın.  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. Tablo için önceden tanımlanmış bir biçim belirtmek için, son satırı `DisplayInWord` aşağıdaki ifadeyle değiştirin ve ardından <kbd>CTRL</kbd>+<kbd>F5</kbd>yazın. Biçim, [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) sabitlerinden herhangi biri olabilir.

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a>Örnek

Aşağıdaki kod tam örneği içerir:

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a>Ayrıca bkz.

- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](./named-and-optional-arguments.md)
