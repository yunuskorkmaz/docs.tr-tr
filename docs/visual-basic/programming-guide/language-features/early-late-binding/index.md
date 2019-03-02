---
title: Erken ve Geç Bağlama (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
  - 'early binding [Visual Basic]'
  - 'objects [Visual Basic], late-bound'
  - 'objects [Visual Basic], early-bound'
  - 'objects [Visual Basic], late bound'
  - 'early binding [Visual Basic], Visual Basic compiler'
  - 'binding [Visual Basic], late and early'
  - 'objects [Visual Basic], early bound'
  - 'Visual Basic compiler, early and late binding'
  - 'late binding [Visual Basic]'
  - 'late binding [Visual Basic], Visual Basic compiler'
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
---
# <a name="early-and-late-binding-visual-basic"></a>Erken ve Geç Bağlama (Visual Basic)
Visual Basic Derleyicisi adlı bir işlem gerçekleştirir `binding` bir nesne bir nesne değişkenine atanan zaman. Bir nesnenin *erken bağlama* onu bir değişkene atandığında bildirilen belirli nesne türünde olması. Erken bağlama nesnelerine derleyicinin bellek ayırma ve uygulama yürütülmeden önce diğer iyileştirmeler gerçekleştirmek izin verin. Örneğin, aşağıdaki kod parçası, türünde bir değişkeni bildirir <xref:System.IO.FileStream>:  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 Çünkü <xref:System.IO.FileStream> bir belirli nesne türü, atanan örnek `FS` erken bağlama.  
  
 Bunun aksine, bir nesnedir *geç bağlama* onu bir değişkene atandığında bildirilen türü olmasını `Object`. Bu tür nesnelerin herhangi bir nesne başvuruları tutmak ancak çok erken bağlanan nesneleri avantajları eksik. Örneğin, aşağıdaki kod parçası tarafından döndürülen bir nesnesini tutacak bir nesne değişkeni bildirir `CreateObject` işlevi:  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a>Erken bağlama avantajları  
 Bunlar daha verimli uygulamalar yield önemli iyileştirmeler yapmak için derleyici izin verdiğinden, mümkün olduğunca erken bağlanan nesneleri kullanmanız gerekir. Erken bağlı nesneler geç bağlama nesnelerini önemli ölçüde daha hızlı ve kodunuzu okunması ve düzenlenmesi hangi türdeki nesneleri tam olarak kullanıldığı belirterek daha kolay hale getirmek. Visual Studio tümleşik geliştirme ortamı (IDE) düzenleme gibi tam olarak hangi tür nesnenin çalıştığınız belirlemek için otomatik kod tamamlama ve dinamik Yardım gibi yararlı özellikleri sağlayan erken bağlama başka bir avantajı, kodu. Bir program derlendiğinde derleyici hatalarını raporlamak için izin verdiği için erken bağlama sayısını ve çalışma zamanı hataları azaltır.  
  
> [!NOTE]
>  Geç bağlama yalnızca olarak bildirilen tür üyelerine erişmek için kullanılabilir `Public`. Olarak bildirilen üyelere erişme `Friend` veya `Protected Friend` bir çalışma zamanı hatası oluşur.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [Nesne ömrü: Nesnelerin nasıl oluşturulduğunu ve yok](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)
