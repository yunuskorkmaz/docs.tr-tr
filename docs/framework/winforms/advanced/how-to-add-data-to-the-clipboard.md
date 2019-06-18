---
title: 'Nasıl yapılır: Panoya Veri Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
ms.openlocfilehash: 4d035dd6611909c9a6b67662d17f80057dc33386
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169959"
---
# <a name="how-to-add-data-to-the-clipboard"></a>Nasıl yapılır: Panoya Veri Ekleme
<xref:System.Windows.Forms.Clipboard> Sınıfı, Windows işletim sistemi Pano özelliğini ile etkileşim kurmak için kullanabileceğiniz yöntemler sağlar. Birçok uygulama Pano verileri için geçici bir deposu olarak kullanın. Örneğin, Word'ün işlemci panoya kes/yapıştır işlemleri sırasında kullanın. Pano, başka bir uygulamadan veri aktarmak için kullanışlıdır.  
  
 Panoya veri ekleme, bu biçimi kullanıyorsanız, diğer uygulamalar verileri tanıyabilmesi veri biçimi belirtebilirsiniz. Ayrıca, potansiyel olarak veri kullanan diğer uygulamalar sayısını artırmak için birden çok farklı biçimlerde panosu için veri ekleyebilirsiniz.  
  
 Pano biçimi alabilmesi bu biçimi kullanan bir uygulamayı ilişkili veri biçimini tanımlayan bir dizedir. <xref:System.Windows.Forms.DataFormats> Sınıfı kullanmanız için önceden tanımlanmış biçim adları sağlar. Ayrıca, kendi biçim adları kullanın veya bir nesne türünü, biçimi kullanabilirsiniz.  
  
 Bir veya birden çok biçimde panoya veri eklemek için <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> yöntemi. Bu yöntem için herhangi bir nesne geçirebilirsiniz, ancak birden çok biçimde veri eklemek için önce veriler ile birden çok biçimde çalışmak üzere tasarlanmış ayrı bir nesne eklemeniz gerekir. Genellikle, verilerinize ekleyeceksiniz bir <xref:System.Windows.Forms.DataObject>, ancak uygulayan herhangi bir türü kullanabilirsiniz <xref:System.Windows.Forms.IDataObject> arabirimi.  
  
 .NET Framework 2.0 sürümünde, temel Pano görevleri daha kolay hale getirmek için tasarlanan yeni yöntemlerle doğrudan panoya veri ekleyebilirsiniz. Metin gibi tek, ortak bir biçimde verilerle çalışırken bu yöntemleri kullanın.  
  
> [!NOTE]
>  Tüm Windows tabanlı uygulamalar, Pano paylaşabilirsiniz. Bu nedenle, başka bir uygulamaya geçtiğinde içeriği değişikliğe tabi olduğu.  
>   
>  <xref:System.Windows.Forms.Clipboard> Sınıfı yalnızca kullanılabilir iş parçacıklarında tek iş parçacığı Grup (STA) moduna ayarlayın. Bu sınıf kullanmak için emin olun, `Main` yöntemi ile işaretlenmiş <xref:System.STAThreadAttribute> özniteliği.  
>   
>  Bir nesne, Panodaki koymak için Serileştirilebilir olmalıdır. Bir tür serileştirilebilir yapmak için kendisiyle işaretlemek <xref:System.SerializableAttribute> özniteliği. Seri hale getirilemeyen bir nesne bir Pano yöntemine geçirirseniz, yöntem bir özel durum olmadan başarısız olur. Seri hale getirme hakkında daha fazla bilgi için bkz: <xref:System.Runtime.Serialization>.  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>Pano tek, ortak bir biçimde veri eklemek için  
  
1. Kullanım <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, veya <xref:System.Windows.Forms.Clipboard.SetText%2A> yöntemi. Bu yöntemler, yalnızca .NET Framework 2.0 sürümünde kullanılabilir.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>Özel bir biçim panoya veri eklemek için  
  
1. Kullanım <xref:System.Windows.Forms.Clipboard.SetData%2A> yöntemi ile bir özel biçim adı. Bu yöntem, yalnızca .NET Framework 2.0 sürümünde kullanılabilir.  
  
     Önceden tanımlanmış biçim adıyla kullanabilirsiniz <xref:System.Windows.Forms.Clipboard.SetData%2A> yöntemi. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>Birden çok biçimde panoya veri ekleme  
  
1. Kullanım <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> yöntemi ve geçişinde bir <xref:System.Windows.Forms.DataObject> verilerinizi içeren. Veri sürümleri panoya eklemek için bu yöntemi kullanın öncesi [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sürükle ve Bırak İşlemleri ve Pano Desteği](drag-and-drop-operations-and-clipboard-support.md)
- [Nasıl yapılır: Panodan veri alma](how-to-retrieve-data-from-the-clipboard.md)
