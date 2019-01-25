---
title: 'Nasıl yapılır: Panodan veri alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
ms.openlocfilehash: 8857ebb5a5c29f8e945ea47c290259c4b787b430
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545718"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>Nasıl yapılır: Panodan veri alma
<xref:System.Windows.Forms.Clipboard> Sınıfı, Windows işletim sistemi Pano özelliğini ile etkileşim kurmak için kullanabileceğiniz yöntemler sağlar. Birçok uygulama Pano verileri için geçici bir deposu olarak kullanın. Örneğin, Word'ün işlemci panoya kes/yapıştır işlemleri sırasında kullanın. Pano, bir uygulamadan diğerine bilgi aktarmak için kullanışlıdır.  
  
 Bazı uygulamalar, potansiyel olarak veri kullanan diğer uygulamalar sayısını artırmak için birden çok biçimde Pano üzerinde verileri depolar. Pano biçimi biçimini tanımlayan bir dizedir. Tanımlanan biçimi kullanan bir uygulama, Panodaki ilişkili verileri alabilirsiniz. <xref:System.Windows.Forms.DataFormats> Sınıfı kullanmanız için önceden tanımlanmış biçim adları sağlar. Ayrıca, kendi biçim adları kullanın veya kendi biçiminde bir nesnenin türünü kullanın. Panoya veri ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Panoya veri ekleme](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md).  
  
 Pano belirli bir biçimde veri içerip içermediğini belirlemek için aşağıdakilerden birini kullanın: `Contains` *biçimi* yöntemleri veya <xref:System.Windows.Forms.Clipboard.GetData%2A> yöntemi. Panodan veri almak için aşağıdakilerden birini kullanın: `Get` *biçimi* yöntemleri veya <xref:System.Windows.Forms.Clipboard.GetData%2A> yöntemi. Bu yöntemler yeni [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
 Pano sürümlerini kullanarak verilere erişmek için daha önceki [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)], kullanın <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> yöntemi ve döndürülen in yöntemlerini çağırabilirsiniz <xref:System.Windows.Forms.IDataObject>. Örneğin, belirli bir biçimde döndürülen nesneyi kullanılabilir olup olmadığını belirlemek için çağrı <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> yöntemi.  
  
> [!NOTE]
>  Tüm Windows tabanlı uygulamalar, Pano sistem paylaşın. Bu nedenle, başka bir uygulamaya geçtiğinde içeriği değişikliğe tabi olduğu.  
>   
>  <xref:System.Windows.Forms.Clipboard> Sınıfı yalnızca kullanılabilir iş parçacıklarında tek iş parçacığı Grup (STA) moduna ayarlayın. Bu sınıf kullanmak için emin olun, `Main` yöntemi ile işaretlenmiş <xref:System.STAThreadAttribute> özniteliği.  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>Tek, ortak bir biçimde panodan veri almak için  
  
1.  Kullanım <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, veya <xref:System.Windows.Forms.Clipboard.GetText%2A> yöntemi. İsteğe bağlı olarak karşılık gelen kullanın `Contains` *biçimi* ilk veri belirli bir biçimde kullanılabilir olup olmadığını belirlemek için yöntemleri. Bu yöntem yalnızca [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>Özel bir biçimde panodan veri almak için  
  
1.  Kullanım <xref:System.Windows.Forms.Clipboard.GetData%2A> yöntemi ile bir özel biçim adı. Bu yöntem yalnızca kullanılabilir [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     Önceden tanımlanmış biçim adıyla kullanabilirsiniz <xref:System.Windows.Forms.Clipboard.SetData%2A> yöntemi. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>Birden çok biçimde panodan veri almak için  
  
1.  Kullanım <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> yöntemi. Sürümlerinde panodan veri almak için bu yöntemi kullanın öncesi [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Sürükle ve Bırak İşlemleri ve Pano Desteği](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
- [Nasıl yapılır: Panoya veri ekleme](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)
