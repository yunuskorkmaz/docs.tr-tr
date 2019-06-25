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
ms.openlocfilehash: 868afc36f08571d16285d0df52f6d1cad8c9c7a6
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348211"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>Nasıl yapılır: Panodan Veri Alma
<xref:System.Windows.Forms.Clipboard> Sınıfı, Windows işletim sistemi Pano özelliğini ile etkileşim kurmak için kullanabileceğiniz yöntemler sağlar. Birçok uygulama Pano verileri için geçici bir deposu olarak kullanın. Örneğin, Word'ün işlemci panoya kes/yapıştır işlemleri sırasında kullanın. Pano, bir uygulamadan diğerine bilgi aktarmak için kullanışlıdır.  
  
 Bazı uygulamalar, potansiyel olarak veri kullanan diğer uygulamalar sayısını artırmak için birden çok biçimde Pano üzerinde verileri depolar. Pano biçimi biçimini tanımlayan bir dizedir. Tanımlanan biçimi kullanan bir uygulama, Panodaki ilişkili verileri alabilirsiniz. <xref:System.Windows.Forms.DataFormats> Sınıfı kullanmanız için önceden tanımlanmış biçim adları sağlar. Ayrıca, kendi biçim adları kullanın veya kendi biçiminde bir nesnenin türünü kullanın. Panoya veri ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Panoya veri ekleme](how-to-add-data-to-the-clipboard.md).  
  
 Pano belirli bir biçimde veri içerip içermediğini belirlemek için aşağıdakilerden birini kullanın: `Contains` *biçimi* yöntemleri veya <xref:System.Windows.Forms.Clipboard.GetData%2A> yöntemi. Panodan veri almak için aşağıdakilerden birini kullanın: `Get` *biçimi* yöntemleri veya <xref:System.Windows.Forms.Clipboard.GetData%2A> yöntemi. Bu yöntemler .NET Framework 2.0 sürümünde yenidir.  
  
 .NET Framework 2. 0'dan önceki sürümleri kullanılarak panodan veri erişmek için <xref:System.Windows.Forms.Clipboard.GetDataObject%2A?displayProperty=nameWithType> yöntemi ve döndürülen in yöntemlerini çağırabilirsiniz <xref:System.Windows.Forms.IDataObject>. Örneğin, belirli bir biçimde döndürülen nesneyi kullanılabilir olup olmadığını belirlemek için çağrı <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> yöntemi.  
  
> [!NOTE]
>  Tüm Windows tabanlı uygulamalar, Pano sistem paylaşın. Bu nedenle, başka bir uygulamaya geçtiğinde içeriği değişikliğe tabi olduğu.  
>   
>  <xref:System.Windows.Forms.Clipboard> Sınıfı yalnızca kullanılabilir iş parçacıklarında tek iş parçacığı Grup (STA) moduna ayarlayın. Bu sınıf kullanmak için emin olun, `Main` yöntemi ile işaretlenmiş <xref:System.STAThreadAttribute> özniteliği.  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>Tek, ortak bir biçimde panodan veri almak için  
  
1. Kullanım <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, veya <xref:System.Windows.Forms.Clipboard.GetText%2A> yöntemi. İsteğe bağlı olarak karşılık gelen kullanın `Contains` *biçimi* ilk veri belirli bir biçimde kullanılabilir olup olmadığını belirlemek için yöntemleri. Bu yöntemler, yalnızca .NET Framework 2.0 sürümünde kullanılabilir.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>Özel bir biçimde panodan veri almak için  
  
1. Kullanım <xref:System.Windows.Forms.Clipboard.GetData%2A> yöntemi ile bir özel biçim adı. Bu yöntem, yalnızca .NET Framework 2.0 sürümünde kullanılabilir.  
  
     Önceden tanımlanmış biçim adıyla kullanabilirsiniz <xref:System.Windows.Forms.Clipboard.SetData%2A> yöntemi. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>Birden çok biçimde panodan veri almak için  
  
1. Kullanım <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> yöntemi. Bu yöntem .NET Framework 2. 0'dan önceki sürümlerde panodan veri almak için kullanmanız gerekir.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sürükle ve Bırak İşlemleri ve Pano Desteği](drag-and-drop-operations-and-clipboard-support.md)
- [Nasıl yapılır: Panoya veri ekleme](how-to-add-data-to-the-clipboard.md)
