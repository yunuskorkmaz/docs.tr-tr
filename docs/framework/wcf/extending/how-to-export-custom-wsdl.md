---
title: 'Nasıl yapılır: Özel WSDL Dışarı Aktarma'
ms.date: 03/30/2017
ms.assetid: 5c1e4b58-b76b-472b-9635-2f80d42a0734
ms.openlocfilehash: 0e8d1079124b981c3408d46040c8d83bf6877dfb
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972094"
---
# <a name="how-to-export-custom-wsdl"></a>Nasıl yapılır: Özel WSDL Dışarı Aktarma

Bu konuda, özel WSDL bilgilerinin nasıl dışarı aktarılacağı açıklanmaktadır. Bunu yapmak için, hizmet tarafından oluşturulan wsdl 'ye özel bilgiler `WsdlDocumentationAttribute` ekleyecek adlı yeni bir kod özniteliği tanımlayacağız.

## <a name="to-export-custom-wsdl-information"></a>Özel WSDL bilgilerini dışarı aktarmak için

1. <xref:System.ServiceModel.Description.IWsdlExportExtension> arabirimini gerçekleştirin. Bu arabirim, aşağıdaki arabirimlerden herhangi birini uygulayan bir sınıfa uygulanabilir: <xref:System.ServiceModel.Description.IOperationBehavior>, <xref:System.ServiceModel.Description.IContractBehavior>veya <xref:System.ServiceModel.Description.IEndpointBehavior>. Ayrıca, öğesinden <xref:System.ServiceModel.Channels.BindingElement>türetilmiş bir sınıfta da uygulanabilir. Bu örnek, <xref:System.ServiceModel.Description.IWsdlExportExtension> uygulayan <xref:System.ServiceModel.Description.IContractBehavior>bir öznitelik sınıfını uygular.

2. <xref:System.ServiceModel.Description.IWsdlExportExtension>iki yöntemi <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29>tanımlar. Bu yöntemler, <xref:System.ServiceModel.Description.WsdlContractConversionContext>üzerinde ek bilgileri değiştirmenize veya eklemenize (ya da her ikisini de eklemenize) izin verir. Bu örnek, <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> yönteminde bir <xref:System.ServiceModel.Description.OperationDescription> nesne koleksiyonu alır ve sonra bir `WsdlDocumentationAttribute`için koleksiyon denetimi boyunca yinelenir. Bir tane bulunursa, özniteliğiyle ilişkili metin ayıklanır, bir Summary öğesi oluşturulur ve Özet öğesi işlemin içine `DocumentationElement` eklenir.

    ```csharp
    public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)
    {
        Console.WriteLine("Inside ExportContract");
        if (context.Contract != null)
        {
            // Set the document element; if this is not done first, there is no XmlElement in the
            // DocumentElement property.
            context.WsdlPortType.Documentation = string.Empty;
            // Contract comments.
            XmlDocument owner = context.WsdlPortType.DocumentationElement.OwnerDocument;
            XmlElement summaryElement = Formatter.CreateSummaryElement(owner, this.Text);
            context.WsdlPortType.DocumentationElement.AppendChild(summaryElement);

            foreach (OperationDescription op in context.Contract.Operations)
            {
                Operation operation = context.GetOperation(op);
                object[] opAttrs = op.SyncMethod.GetCustomAttributes(typeof(WsdlDocumentationAttribute), false);
                if (opAttrs.Length == 1)
                {
                    string opComment = ((WsdlDocumentationAttribute)opAttrs[0]).Text;

                    // This.Text returns the string for the operation-level attributes.
                    // Set the doc element; if this is not done first, there is no XmlElement in the
                    // DocumentElement property.
                    operation.Documentation = String.Empty;

                    XmlDocument opOwner = operation.DocumentationElement.OwnerDocument;
                    XmlElement newSummaryElement = Formatter.CreateSummaryElement(opOwner, opComment);
                    operation.DocumentationElement.AppendChild(newSummaryElement);
                }
            }
        }
    }
    ```

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, `WsdlDocumentationAttribute` sınıfının tam uygulamasını gösterir.

```csharp
public class WsdlDocumentationAttribute : Attribute, IContractBehavior, IWsdlExportExtension
{
string text;
       XmlElement customWsdlDocElement = null;
public WsdlDocumentationAttribute(string text)
{ this.text = text;}

       public WsdlDocumentationAttribute(XmlElement wsdlDocElement)
        { this.customWsdlDocElement = wsdlDocElement; }

        public XmlElement WsdlDocElement
        {
            get { return this.customWsdlDocElement; }
            set { this.customWsdlDocElement = value; }
        }
       public string Text
{
get { return this.text; }
set { this.text = value; }
}

     public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)
{
          Console.WriteLine("Inside ExportContract");
if (context.Contract != null)
{
                // Set the document element; if this is not done first, there is no XmlElement in the
                // DocumentElement property.
                context.WsdlPortType.Documentation = string.Empty;
                // Contract comments.
                XmlDocument owner = context.WsdlPortType.DocumentationElement.OwnerDocument;
                XmlElement summaryElement = Formatter.CreateSummaryElement(owner, this.Text);
                context.WsdlPortType.DocumentationElement.AppendChild(summaryElement);

                foreach (OperationDescription op in context.Contract.Operations)
                {
                    Operation operation = context.GetOperation(op);
                    object[] opAttrs = op.SyncMethod.GetCustomAttributes(typeof(WsdlDocumentationAttribute), false);
                    if (opAttrs.Length == 1)
                    {
                        string opComment = ((WsdlDocumentationAttribute)opAttrs[0]).Text;

                        // This.Text returns the string for the operation-level attributes.
                        // Set the document element; if this is not done first, there is no XmlElement in the
                        // DocumentElement property.
                        operation.Documentation = String.Empty;

                        XmlDocument opOwner = operation.DocumentationElement.OwnerDocument;
                        XmlElement newSummaryElement = Formatter.CreateSummaryElement(opOwner, opComment);
                        operation.DocumentationElement.AppendChild(newSummaryElement);
                    }
                }
            }
        }

public void ExportEndpoint(WsdlExporter exporter, WsdlEndpointConversionContext context)
        {
            Console.WriteLine("ExportEndpoint called.");
        }

        public void AddBindingParameters(ContractDescription description, ServiceEndpoint endpoint, BindingParameterCollection parameters)
        { return; }

        public void ApplyClientBehavior(ContractDescription description, ServiceEndpoint endpoint, ClientRuntime client)
        { return; }

        public void ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)
        { return; }

        public void Validate(ContractDescription description, ServiceEndpoint endpoint) { return; }
    }

  public class Formatter
  {

#region Utility Functions

    public static XmlElement CreateSummaryElement(XmlDocument owningDoc, string text)
    {
      XmlElement summaryElement = owningDoc.CreateElement("summary");
      summaryElement.InnerText = text;
      return summaryElement;
    }

public static CodeCommentStatementCollection FormatComments(string text)
{
      /*
       * Note that in Visual C# the XML comment format absorbs a
       * documentation element with a line break in the middle. This sample
       * could take an XmlElement and create code comments in which
       * the element never had a line break in it.
      */

      CodeCommentStatementCollection collection = new CodeCommentStatementCollection();
collection.Add(new CodeCommentStatement("From WsdlDocumentation:", true));
collection.Add(new CodeCommentStatement(String.Empty, true));

foreach (string line in WordWrap(text, 80))
{
collection.Add(new CodeCommentStatement(line, true));
}

collection.Add(new CodeCommentStatement(String.Empty, true));
return collection;
}

public static Collection<string> WordWrap(string text, int columnWidth)
{
Collection<string> lines = new Collection<string>();
System.Text.StringBuilder builder = new System.Text.StringBuilder();

string[] words = text.Split(' ');
foreach (string word in words)
{
if ((builder.Length > 0) && ((builder.Length + word.Length + 1) > columnWidth))
{
lines.Add(builder.ToString());
builder = new System.Text.StringBuilder();
}
builder.Append(word);
builder.Append(' ');
}
lines.Add(builder.ToString());

return lines;
}

#endregion

    public static XmlElement CreateReturnsElement(XmlDocument owner, string p)
    {
      XmlElement returnsElement = owner.CreateElement("returns");
      returnsElement.InnerText = p;
      return returnsElement;
    }
  }
```

## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veriler](../../../../docs/framework/wcf/feature-details/metadata.md)
