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
ms.openlocfilehash: e06fb509bed32df0c18f2a03ae89765b3334b2c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>Nasıl yapılır: Panodan Veri Alma
<xref:System.Windows.Forms.Clipboard> Sınıfı Windows işletim sistemi Pano özelliği ile etkileşim kurmak için kullanabileceğiniz yöntemler sağlar. Birçok uygulama Pano verileri için geçici depo olarak kullanın. Örneğin, sözcük işlemci kesme ve yapıştırma işlemleri sırasında Panosu'nu kullanın. Pano, bir uygulamadan diğerine bilgileri aktarmak için yararlıdır.  
  
 Bazı uygulamalar, veriler kullanabilmeniz için diğer uygulamaları sayısını artırmak için Pano'ya çoklu biçimlerde verileri depolar. Pano biçimi biçimini tanımlayan bir dizedir. Tanımlanan biçimi kullanan bir uygulamayı Pano'daki ilişkili veri alabilir. <xref:System.Windows.Forms.DataFormats> Sınıfı kullanmanız için önceden tanımlanmış biçim adlarının sağlar. Ayrıca, kendi biçim adları kullanın veya bir nesnenin türünü, biçimi kullanın. Panoya veri ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: panoya veri ekleme](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md).  
  
 Pano belirli bir biçimde veri içerip içermediğini belirlemek için aşağıdakilerden birini kullanmak `Contains` *biçimi* yöntemleri veya <xref:System.Windows.Forms.Clipboard.GetData%2A> yöntemi. Pano verilerini almak için aşağıdakilerden birini kullanın `Get` *biçimi* yöntemleri veya <xref:System.Windows.Forms.Clipboard.GetData%2A> yöntemi. Bu yöntemler yeni [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
 Sürümleri kullanarak panodan verilere erişme öncesi [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)], kullanın <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> yöntemi ve dönen yöntemlerini çağıran <xref:System.Windows.Forms.IDataObject>. Örneğin, belirli bir biçimde nesnesine döndürülen kullanılabilir olup olmadığını belirlemek için arama <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> yöntemi.  
  
> [!NOTE]
>  Tüm Windows tabanlı uygulamalar Pano sistem paylaşır. Bu nedenle, başka bir uygulamaya geçiş yaptığınızda içeriği değiştirilebilir ' dir.  
>   
>  <xref:System.Windows.Forms.Clipboard> Sınıfı yalnızca kullanılabilir iş parçacıklarında tek iş parçacığı Grup (STA) modu olarak ayarlanmış. Bu sınıf kullanmak için emin olun, `Main` yöntemi ile işaretlenmiş <xref:System.STAThreadAttribute> özniteliği.  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>Tek, ortak bir biçimde panodan veri almak için  
  
1.  Kullanım <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, veya <xref:System.Windows.Forms.Clipboard.GetText%2A> yöntemi. İsteğe bağlı olarak, karşılık gelen kullanmak `Contains` *biçimi* ilk veri belirli bir biçimde kullanılabilir olup olmadığını belirlemek için yöntem. Bu yöntem yalnızca kullanılabilir [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>Özel bir biçim panoya veri almak için  
  
1.  Kullanım <xref:System.Windows.Forms.Clipboard.GetData%2A> yöntemi bir özel biçim adına sahip. Bu yöntem yalnızca kullanılabilir [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     Önceden tanımlanmış biçim adıyla de kullanabilirsiniz <xref:System.Windows.Forms.Clipboard.SetData%2A> yöntemi. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>Çoklu biçimlerde panodan veri almak için  
  
1.  Kullanım <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> yöntemi. Sürümlerinde panodan veri almak için bu yöntemi kullanın öncesi [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sürükle ve Bırak İşlemleri ve Pano Desteği](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [Nasıl yapılır: Panoya Veri Ekleme](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)
