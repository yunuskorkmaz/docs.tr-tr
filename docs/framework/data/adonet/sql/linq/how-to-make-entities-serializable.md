---
title: 'Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: f4528cab21ac678f5d06717d0ce6e7ff7e77d3e4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203507"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="ed17e-102">Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ed17e-102">How to: Make Entities Serializable</span></span>

<span data-ttu-id="ed17e-103">Kodunuzu oluştururken varlıkları seri hale getirilebilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed17e-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="ed17e-104">Varlık sınıfları özniteliğiyle <xref:System.Runtime.Serialization.DataContractAttribute> ve özniteliğiyle birlikte sütunlar halinde tasarlanmalıdır <xref:System.Runtime.Serialization.DataMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ed17e-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="ed17e-105">Visual Studio kullanan geliştiriciler bu amaçla Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ed17e-105">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="ed17e-106">SQLMetal komut satırı aracını kullanıyorsanız, **/Serialization** seçeneğini `unidirectional` bağımsız değişkeniyle birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="ed17e-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="ed17e-107">Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="ed17e-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed17e-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed17e-108">Example</span></span>  

 <span data-ttu-id="ed17e-109">Aşağıdaki SQLMetal komut satırları, serileştirilebilir varlıkları olan dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ed17e-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed17e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed17e-110">See also</span></span>

- [<span data-ttu-id="ed17e-111">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="ed17e-111">Serialization</span></span>](serialization.md)
- [<span data-ttu-id="ed17e-112">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ed17e-112">Creating the Object Model</span></span>](creating-the-object-model.md)
