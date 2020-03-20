---
title: "Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma"
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 91e89dbf36024c31f4afcd9b6d956944baf13576
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174192"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma
Bu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]konu, uygulamanızın gereksinimlerine bağlı olarak, verileri bağlamak için kullanılabilir hale getirebileceğiniz çeşitli yolları tartışır.  
  
## <a name="example"></a>Örnek  
 Bağlamak istediğiniz ortak bir dil çalışma zamanı (CLR) nesneniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]varsa, nesneyi bağlama için kullanılabilir hale getirmenin bir yolu, `x:Key`nesneyi kaynak olarak tanımlamak ve bir . Aşağıdaki örnekte, dize `Person` özelliği ne adlandırılmış `PersonName`bir nesne var. Nesne `Person` `<src>` (öğeyi içeren vurgulanan çizgide) adlı `SDKSample`ad alanında tanımlanır.  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Daha sonra, <xref:System.Windows.Controls.TextBlock> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `<TextBlock>` öğeyi içeren vurgulanmış satırda olduğu gibi denetimi nesneye bağlayabilirsiniz.
  
 Alternatif olarak, aşağıdaki <xref:System.Windows.Data.ObjectDataProvider> örnekte olduğu gibi sınıfı kullanabilirsiniz:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Öğeyi içeren vurgulanmış satır ın gösterdiği gibi, `<TextBlock>` bağlamayı aynı şekilde tanımlarsınız.  
  
 Bu özel örnekte, sonuç aynıdır: metin <xref:System.Windows.Controls.TextBlock> içeriği `Joe`ile bir var. Ancak, <xref:System.Windows.Data.ObjectDataProvider> sınıf bir yöntemin sonucuna bağlama yeteneği gibi işlevsellik sağlar. Sağladığı işlevselliğe ihtiyacınız <xref:System.Windows.Data.ObjectDataProvider> varsa sınıfı kullanmayı seçebilirsiniz.  
  
 Ancak, zaten oluşturulmuş bir nesneye bağlanınca, aşağıdaki örnekte olduğu gibi `DataContext` kodu ayarlamanız gerekir.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Sınıfı kullanarak bağlamak için XML verilerine <xref:System.Windows.Data.XmlDataProvider> erişmek için, [XMLDataProvider ve XPath Sorguları kullanarak XML Veri bind](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)bakın. Sınıfı kullanarak bağlamak için XML verilerine <xref:System.Windows.Data.ObjectDataProvider> erişmek için [XML Sorgu Sonuçları için XDocument, XElement veya LINQ'a](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)bağlan'a bakın.  
  
 Bağlandığınız verileri belirtmenin birçok yolu hakkında bilgi için [bkz.](how-to-specify-the-binding-source.md) Bağlama için ne tür veri bağlayabilirsiniz veya kendi ortak dil çalışma zamanı (CLR) nesneleri nasıl uygulayacağınız hakkında bilgi [için](binding-sources-overview.md)bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Nasıl Dır Konular](data-binding-how-to-topics.md)
