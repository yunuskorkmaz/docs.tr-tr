---
title: "Nasıl yapılır: Panoya Veri Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47858af6d4e3dc5f29632c5a74f2431a2cc200b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-data-to-the-clipboard"></a>Nasıl yapılır: Panoya Veri Ekleme
<xref:System.Windows.Forms.Clipboard> Sınıfı Windows işletim sistemi Pano özelliği ile etkileşim kurmak için kullanabileceğiniz yöntemler sağlar. Birçok uygulama Pano verileri için geçici depo olarak kullanın. Örneğin, sözcük işlemci kesme ve yapıştırma işlemleri sırasında Panosu'nu kullanın. Pano, bir uygulamadan başka bir veri aktarmak için yararlıdır.  
  
 Panoya veri eklediğinizde, bu biçimi kullanıyorsanız diğer uygulamaların veri tanıyabilmesi veri biçimi belirtebilirsiniz. Veri kullanabilmeniz için diğer uygulamaları sayısını artırmak için panoya birden çok farklı biçimlerde verileri de ekleyebilirsiniz.  
  
 Böylece bu biçimi kullanan bir uygulamayı ilişkili veri biçimini tanımlayan bir dize bir Pano biçimidir. <xref:System.Windows.Forms.DataFormats> Sınıfı kullanmanız için önceden tanımlanmış biçim adlarının sağlar. Ayrıca, kendi biçim adları kullanın veya bir nesne türünü, biçimi kullanabilirsiniz.  
  
 Bir veya birden çok biçimlerde Pano veri eklemek için kullanın <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> yöntemi. Bu yöntem herhangi bir nesne geçirebilirsiniz ancak çoklu biçimlerde veri eklemek için önce verileri birden çok biçim ile çalışmak üzere tasarlanmış ayrı bir nesne eklemeniz gerekir. Genellikle, verilerinizi ekleyecek bir <xref:System.Windows.Forms.DataObject>, ancak uygulayan herhangi bir türü kullanabilirsiniz <xref:System.Windows.Forms.IDataObject> arabirimi.  
  
 İçinde [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], temel Pano görevleri kolaylaştırmak için tasarlanmış yeni yöntemlerle doğrudan panoya verileri ekleyebilirsiniz. Metin gibi tek, ortak biçiminde verilerle çalışırken bu yöntemleri kullanın.  
  
> [!NOTE]
>  Tüm Windows tabanlı uygulamalar Pano paylaşır. Bu nedenle, başka bir uygulamaya geçiş yaptığınızda içeriği değiştirilebilir ' dir.  
>   
>  <xref:System.Windows.Forms.Clipboard> Sınıfı yalnızca kullanılabilir iş parçacıklarında tek iş parçacığı Grup (STA) modu olarak ayarlanmış. Bu sınıf kullanmak için emin olun, `Main` yöntemi ile işaretlenmiş <xref:System.STAThreadAttribute> özniteliği.  
>   
>  Bir nesne Pano'ya yerleştir kendisine için Serileştirilebilir olmalıdır. Türü seri hale getirilebilir yapmak için kendisiyle işaretlemek <xref:System.SerializableAttribute> özniteliği. Bir Pano yönteme serileştirilebilir olmayan bir nesne geçirirseniz, yöntem bir özel durum atma olmadan başarısız olur. Seri hale getirme hakkında daha fazla bilgi için bkz: <xref:System.Runtime.Serialization>.  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>Tek, ortak bir biçimde Pano veri eklemek için  
  
1.  Kullanım <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, veya <xref:System.Windows.Forms.Clipboard.SetText%2A> yöntemi. Bu yöntem yalnızca kullanılabilir [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>Özel bir biçim panoya veri eklemek için  
  
1.  Kullanım <xref:System.Windows.Forms.Clipboard.SetData%2A> yöntemi bir özel biçim adına sahip. Bu yöntem yalnızca kullanılabilir [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     Önceden tanımlanmış biçim adıyla de kullanabilirsiniz <xref:System.Windows.Forms.Clipboard.SetData%2A> yöntemi. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>Birden çok biçim panoya veri eklemek için  
  
1.  Kullanım <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> yöntemi ve geçişinde bir <xref:System.Windows.Forms.DataObject> verilerinizi içeren. Sürümleri panoya veri eklemek için bu yöntemi kullanın öncesi [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sürükle ve bırak işlemleri ve Pano desteği](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [Nasıl yapılır: panodan veri alma](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)
