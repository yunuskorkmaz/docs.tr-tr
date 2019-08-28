---
title: 'Nasıl yapılır: Panodan Veri Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
ms.openlocfilehash: ca24615049abcc145698c033f31e6c98a38253bf
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040562"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>Nasıl yapılır: Panodan Veri Alma

Sınıfı <xref:System.Windows.Forms.Clipboard> , Windows işletim sistemi Pano özelliğiyle etkileşim kurmak için kullanabileceğiniz yöntemler sağlar. Birçok uygulama, pano 'Yu veri için geçici bir depo olarak kullanır. Örneğin, Word işlemcileri kes ve yapıştır işlemleri sırasında panoyu kullanır. Pano, bilgileri bir uygulamadan diğerine aktarmak için de kullanışlıdır.

Bazı uygulamalar, verileri potansiyel olarak kullandığımız diğer uygulamaların sayısını artırmak için panodaki verileri birden çok biçimde depolar. Pano biçimi biçimi tanımlayan bir dizedir. Tanımlı biçimi kullanan bir uygulama, panodaki ilişkili verileri alabilir. Sınıfı <xref:System.Windows.Forms.DataFormats> , kullanım için önceden tanımlanmış biçim adları sağlar. Kendi biçim adlarınızı de kullanabilir veya bir nesnenin türünü biçimi olarak kullanabilirsiniz. Panoya veri ekleme hakkında daha fazla bilgi için bkz [. nasıl yapılır: Panoya](how-to-add-data-to-the-clipboard.md)veri ekleyin.

Panonun belirli bir biçimde veri içerip içermediğini anlamak için `Contains` *Format* yöntemlerinden birini veya <xref:System.Windows.Forms.Clipboard.GetData%2A> yöntemini kullanın. Panodan verileri almak için `Get` *Format* yöntemlerinden birini veya <xref:System.Windows.Forms.Clipboard.GetData%2A> yöntemini kullanın. Bu yöntemler .NET Framework 2,0 ' de yenidir.

.NET Framework 2,0 ' den önceki sürümleri kullanarak panodaki verilere erişmek için, <xref:System.Windows.Forms.Clipboard.GetDataObject%2A?displayProperty=nameWithType> yöntemini kullanın ve döndürülen <xref:System.Windows.Forms.IDataObject>Yöntemleri çağırın. Belirli bir biçimin döndürülen nesnede kullanılabilir olup olmadığını belirleme, örneğin, <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> yöntemini çağırın.

> [!NOTE]
> Tüm Windows tabanlı uygulamalar sistem panosunu paylaşır. Bu nedenle, başka bir uygulamaya geçtiğinizde içerik değişebilir.
>
> <xref:System.Windows.Forms.Clipboard> Sınıfı yalnızca tek iş parçacığı apartmanı (STA) moduna ayarlanmış iş parçacıklarında kullanılabilir. Bu sınıfı kullanmak için `Main` yönteminizin <xref:System.STAThreadAttribute> özniteliğiyle işaretlendiğinden emin olun.

### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>Panodaki verileri tek, ortak bir biçimde almak için

1. ,, Veya metodunu<xref:System.Windows.Forms.Clipboard.GetText%2A> kullanın. <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A> <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A> <xref:System.Windows.Forms.Clipboard.GetImage%2A> İsteğe bağlı olarak, verilerin `Contains`belirli bir biçimde kullanılabilir olup olmadığını anlamak için önce karşılık gelen *Biçim* yöntemlerini kullanın. Bu yöntemler yalnızca .NET Framework 2,0 ' de kullanılabilir.

    [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
    [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]

### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>Panodan verileri özel bir biçimde almak için

1. <xref:System.Windows.Forms.Clipboard.GetData%2A> Yöntemi özel biçim adıyla kullanın. Bu yöntem yalnızca .NET Framework 2,0 ' de kullanılabilir.

    Önceden tanımlanmış biçim adlarını <xref:System.Windows.Forms.Clipboard.SetData%2A> yöntemiyle de kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DataFormats>.

    [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
    [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>Panodan birden çok biçimdeki verileri almak için

1. <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> Yöntemini kullanın. .NET Framework 2,0 ' den önceki sürümlerde verileri panodan almak için bu yöntemi kullanmanız gerekir.

    [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
    [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

## <a name="see-also"></a>Ayrıca bkz.

- [Sürükle ve Bırak İşlemleri ve Pano Desteği](drag-and-drop-operations-and-clipboard-support.md)
- [Nasıl yapılır: Panoya veri ekleme](how-to-add-data-to-the-clipboard.md)
